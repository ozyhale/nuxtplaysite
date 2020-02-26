<template>
  <div class="container">
    <div>
      <h1 class="title">
        Ozy's Nuxt Play Site
      </h1>
      <h2 class="subtitle">
        Just my play-site for using NuxtJS
      </h2>
      <div class="links">
        <nuxt-link to="/">
          <span class="mainLink">Home</span>
        </nuxt-link> | 
        <nuxt-link to="/routing">
          <span class="mainLink">Routing</span>
        </nuxt-link> | 
        <nuxt-link to="/budgeting101">
          <span class="mainLink">Budgeting 101</span>
        </nuxt-link> | 
        <nuxt-link to="/about">
          <span class="mainLink">About</span>
        </nuxt-link> | 
        <nuxt-link to="/contact">
          <span class="mainLink">Contact</span>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>

export default {

}
</script>

<style scoped>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
  font-size: 26px;
  color: #35495e;
}

.mainLink:hover{
  @apply text-blue-600;
}
</style>
