<script>

export default {
  // Название компонента
  name: 'TestComponent',

  // Подключаемые компоненты
  components: {},

  // Получение данных из родительского элемента
  props: ['name', 'surname', 'age',],

  // Переменные
  data() {
    return {
      var_test_comp: 'Переменная тестового компонента',
    }
  },

  // Функции
  methods: {
    // Слово с заглавной буквы
    capitalizeFirstLetter(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    }
  },

  // Вычисляемые свойства
  computed: {},

}

</script>

<template>

  <h2>Тестовый компонент</h2>

  <div>

    <p>{{ var_test_comp }}</p>
    <br>
    <br>

    <!--Передача данных в дочерний компонент из родительского во Vue-->
    <p>Передача данных в дочерний компонент из родительского</p>
    <br>
    <p>Имя: {{ this.capitalizeFirstLetter(name) }}</p>
    <p>Фамилия: {{ surname.toUpperCase() }}</p>
    <p>Возраст: {{ age }}</p>


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