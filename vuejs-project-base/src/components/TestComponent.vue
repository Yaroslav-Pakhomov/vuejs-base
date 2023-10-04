<script>

export default {
  // Название компонента
  name: 'TestComponent',

  // Подключаемые компоненты
  components: {},

  // Получение данных из родительского элемента
  props: ['name', 'surname', 'age', 'arg_arr', 'arg_obj', 'arg_bool',],

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
    <br>
    <br>

    <!--Передача данных любого типа в дочерний компонент из родительского во Vue-->
    <p>Передача данных любого типа в дочерний компонент из родительского</p>
    <br>

    <p>
      {{ arg_arr }}
      <br>
      <ul>
        <li v-for="(elem, index) in arg_arr" :key="index">
          Индекс - {{ index }}, элемент - {{ elem }}
        </li>
      </ul>
    </p>
    <br>

    <p>
      {{ arg_obj }}
      <br>
      <ul>
        <li v-for="(obj, key, index) in arg_obj" :key="key">
          Индекс - {{ index }}, ключ - {{ key }}, объект - {{ obj }}
        </li>
      </ul>
    </p>
    <br>

    <p>{{ arg_bool }}</p>


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