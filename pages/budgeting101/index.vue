<template>
  <div class="container">
    <ul class="list-decimal">
      <li v-for="(list, key) in lists" :key="key">
        <nuxt-link :to="'/budgeting101/edit/' + key">{{list.name}}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    let lists = await $axios.$get('/budget_list.json');
    return {
      lists : lists
    }
  }
}
</script>

<style scoped>

</style>
