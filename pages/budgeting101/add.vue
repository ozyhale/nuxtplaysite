<template>
  <div class="container">
    <div>
      <b-field horizontal label="Name">
        <b-input custom-class="w-1/2"></b-input>
      </b-field>
      <b-field horizontal><!-- Label left empty for spacing -->
        <div class="control">
          <b-button class="button" @click.prevent="showAddItemModal">Add Item</b-button>
        </div>
      </b-field>
    </div>
  </div>
</template>

<script>
import addItemModal from '~/components/budgeting101/addItemModal.vue'

export default {
  components: {
    addItemModal
  },
  data(){
    return {
      name : "",
      list : []
    }
  },
  methods: {
    showAddItemModal(){
      this.$buefy.modal.open({
          parent: this,
          component: addItemModal,
          trapFocus: true,
          hasModalCard : true
      });
    }
  }
}
</script>

<style scoped>

</style>
