<template>
  <div class="container">
    <itemForm :listName="listName" :listList="listList" :listId="listId" />
  </div>
</template>

<script>
import itemForm from '~/components/budgeting101/itemForm.vue';
export default {
  async asyncData({ params, $axios }){
    const list = await $axios.$get(`/budget_list/${params.id}.json`);
    return{
      listId : params.id,
      listName : list.name,
      listList : list.list
    }
  },
  components : {
    itemForm
  }
}
</script>

<style scoped>

</style>
