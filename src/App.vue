<template>
  <div id="app">
    <keep-alive exclude="Detaill">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
</style>
