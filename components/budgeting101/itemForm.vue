<template>
  <div class="container">
    <form @submit.prevent="toggleShowItemModal(true, 'add')">
      <b-field horizontal label="Name">
        <b-input custom-class="w-1/2" :ref="'name'" v-model="name"></b-input>
      </b-field>
      <b-field horizontal><!-- Label left empty for spacing -->
        <div class="control">
          <b-button class="button" native-type="submit" type="is-small">Add Item</b-button>
        </div>
      </b-field>
      <b-field horizontal>
        <div class="w-1/2">
          <b-table :data="list" :columns="table.columns" narrowed bordered :selected.sync="table.selected" @dblclick="toggleShowItemModal(true, 'edit')">
            <template slot="empty">
                <section class="section">
                  <div class="content has-text-grey has-text-centered">
                    <p>
                      <b-icon
                          icon="emoticon-sad"
                          size="is-large">
                      </b-icon>
                    </p>
                    <p>Nothing here.</p>
                  </div>
                </section>
            </template>
            <template slot="footer">
                <div class="has-text-right">
                    Total : {{totalCost}}
                </div>
            </template>
          </b-table>
        </div>
      </b-field>
      <b-field horizontal><!-- Label left empty for spacing -->
        <div class="relative control w-1/2">
          <b-button type="is-primary" class="absolute inset-y-0 right-0" @click.prevent="saveList" :loading="loading" :disabled="loading">Save</b-button>
        </div>
      </b-field>
    </form>

    <b-modal :active.sync="itemModalActive" :width="320" scroll="keep">
      <form @submit.prevent="saveItem">
        <div class="modal-card" style="width: auto">
          <header class="modal-card-head">
            {{modalHeader}}
          </header>
          <section class="modal-card-body">
            <b-field horizontal label="Name">
                <b-input v-model="item.name" :ref="'itemName'"></b-input>
            </b-field>
            <b-field horizontal label="Cost">
                <b-input v-model="item.cost" type="number" value="0"></b-input>
            </b-field>
          </section>
          <footer class="modal-card-foot">
            <button class="button" type="button" @click.prevent="toggleShowItemModal(false)">Close</button>
            <button class="button" type="button" @click.prevent="deleteItem" >Delete</button>
            <button class="button is-primary" type="submit">Save</button>
          </footer>
        </div>
      </form>
    </b-modal>
  </div>
</template>

<script>

export default {
  props : ['listId', 'listName', 'listList'],
  data(){
    return {
      id : this.listId,
      name : this.listName,
      list : this.listList,

      itemModalActive : false,
      modalHeader : 'Add',

      loading : false,
      
      item : {
        name : "",
        cost : 0
      },

      table : {
        selected : null,
        columns : [
          {
            field: 'name',
            label: 'Name',
          },
          {
            field: 'cost',
            label: 'Cost',
            numeric: true
          }
        ]
      }
    }
  },
  mounted(){
    this.$refs.name.$el.children[0].focus();
  },
  computed: {
    totalCost(){
      let total = 0;
      this.list.forEach(function (v, i){
        total += parseInt(v.cost);
      });
      return total;
    }
  },
  methods: {

    toggleShowItemModal(toggle, action){

      this.itemModalActive = toggle;

      if(action !== undefined){
        //add item
        if(action == 'add'){
          this.modalHeader = "Add";
          this.item = {
            name : "",
            cost : 0
          }
        }else if(action == 'edit'){
          this.modalHeader = "Edit";
          this.item = this.table.selected
        }
        
        let instance = this;

        this.$nextTick().then(function (){
          instance.$refs.itemName.$el.children[0].focus()
        });
      }
    },

    saveItem(){

      //add item
      if(this.table.selected === null){
        this.list.push(this.item);

        this.item = {
          name : "",
          cost : 0
        }

        this.$refs.itemName.$el.children[0].focus();

      //edit item
      }else{
        this.table.selected = null;
        this.toggleShowItemModal(false);
      }
    },

    async saveList(){
      if(this.list.length > 0 && this.name != ""){
        this.loading = true;

        let prepareList = {
          name : this.name,
          list: this.list
        }

        if(this.id == ""){
          await this.$axios.$post('/budget_list.json', prepareList);
        }else{
          await this.$axios.$put(`/budget_list/${this.id}.json`, prepareList);
        }

        this.loading = false;
        this.$router.push("/budgeting101");
      }else{
        this.$buefy.snackbar.open({
          message: 'Please provide a name and some list',
          type: 'is-warning',
          position: 'is-top'
        });
      }
    }
  }
}
</script>

<style scoped>

</style>
