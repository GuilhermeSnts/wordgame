<template>
  <div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    a: ""
  })
};
</script>

<style lang="sass">
body
  background: #FAF5E1
</style>
