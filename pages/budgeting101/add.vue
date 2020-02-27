<template>
  <div class="container">
    <itemForm listId="" listName="" :listList="[]" />
  </div>
</template>

<script>
import itemForm from '~/components/budgeting101/itemForm.vue';
export default {
  components : {
    itemForm
  }
}
</script>

<style scoped>

</style>
