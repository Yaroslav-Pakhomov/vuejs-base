<script>
export default {
  name: 'AppTest',

  // Переменные
  data () {
    return {
      name: 'John',
      surname: 'Smith',
    }
  },


}
</script>

<template>
  <div class="container">
    <h2 class="green">
      Hello, World AppTest!
    </h2>
    <p>{{ name }}</p>
    <p>{{ surname }}</p>
  </div>
</template>

<style scoped>
div.container {
  margin-top: 40px;
  margin-bottom: 40px;
}

h2 {
  text-align: center;
}
p {
  text-align: center;
}
</style>