<template>
  <div class="container">
    {{breadcrumbs}}
  </div>
</template>

<script>

export default {
  data (){
    return {
      breadcrumbs: this.$route.path.replace(/\//g, " > ")
    }
  }
}
</script>

<style>

</style>
