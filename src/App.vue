<script>
export default {
  data: () => ({
    jsFrameworks: ["react.js", "vue.js", "angular"]
  }),
  mounted() {
    setTimeout(() => {
    this.jsFrameworks.push("svelte.js")
    }, 3000)
  }
};
</script>

<template>
  <h1>Hello World</h1>
  <tags-input :selected-tags="jsFrameworks" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  color: blue;
}

</style>
