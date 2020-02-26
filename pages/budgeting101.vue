<template>
  <div class="container pt-5">
    <ul class="flex pb-10">
      <li class="mr-6">
        <nuxt-link class="text-blue-500 hover:text-blue-800" href="#" to="/">Home</nuxt-link>
      </li>
      <li class="mr-6">
        <nuxt-link class="text-blue-500 hover:text-blue-800" href="#" to="/budgeting101">Lists</nuxt-link>
      </li>
      <li class="mr-6">
        <nuxt-link class="text-blue-500 hover:text-blue-800" href="#" to="/budgeting101/add">Add List</nuxt-link>
      </li>
    </ul>
    <nuxt-child/>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped></style>
