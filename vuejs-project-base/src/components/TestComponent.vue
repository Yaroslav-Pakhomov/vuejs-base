<script>

export default {
  // Название компонента
  name: 'TestComponent',

  // Подключаемые компоненты
  components: {},

  // Получение данных из родительского элемента
  props: {
    name: String,
    surname: String,
    age: String,
    arg_arr: Array,
    arg_obj: Object,
    arg_bool: Boolean,
    parent_name: String,
    parent_surname: String,
    parent_age: Number,
    parent_salary: Number,

    // Типы свойств
    // title: String,
    // likes: Number,
    // isPublished: Boolean,
    // commentIds: Array,
    // author: Object,
    // callback: Function,
    // contactsPromise: Promise // или любой другой конструктор
  },

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
    <br>
    <br>

    <!--Передача свойств объекта data в дочерний компонент из родительского во Vue-->
    <p>Передача свойств объекта data в дочерний компонент из родительского</p>
    <br>

    <p>Имя: {{ this.capitalizeFirstLetter(parent_name) }}</p>
    <p>Фамилия: {{ parent_surname.toUpperCase() }}</p>
    <p>Возраст: {{ parent_age }}</p>
    <p>Зарплата: {{ parent_salary }}</p>

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