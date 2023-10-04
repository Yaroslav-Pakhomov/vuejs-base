<script>

export default {
  // Название компонента
  name: 'TestComponent',

  // Подключаемые компоненты
  components: {},

  // Переменные
  data() {
    return {
      var_test_comp: 'Переменная тестового компонента',
    }
  },

  // Функции
  methods: {},

  // Вычисляемые свойства
  computed: {},

}

</script>

<template>

  <h2>Тестовый компонент</h2>

  <div>

    <p>{{ var_test_comp }}</p>
    <br>

  </div>
  <br>
  <br>
  <br>
  <br>
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