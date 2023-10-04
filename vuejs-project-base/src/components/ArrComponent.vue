<script>
export default {
  name: 'ArrComponent',

  props: {
    name: String,
    surname: String,
    age: Number,
    salary: Number,
    capitalizeFirstLetter: Function,
  },

  data() {
    return {}
  },

  methods: {},

  computed: {},
}
</script>

<template>

  <h2>Компонент цикла</h2>

  <div>

    <p>Имя: {{ capitalizeFirstLetter(name) }}</p>
    <p>Фамилия: {{ surname.toUpperCase() }}</p>
    <p>Возраст: {{ age }}</p>
    <p>Зарплата: {{ salary }}</p>

  </div>
  <br>

</template>

<style scoped>

h2 {
  text-align: center;
}

p {
  text-align: center;
}

</style>