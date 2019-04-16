<template>
  <h1>{{ title }}</h1>
</template>

<script>
export default {
  name: 'AppTitle',
  data () {
    return {
      title: 'A Todo List for Learning Vue'
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-align: center;
  color: #42b983;
  margin-bottom: 30px;
}
</style>
