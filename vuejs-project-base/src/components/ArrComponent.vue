<script>
export default {
  name: 'ArrComponent',

  props: {
    name: String,
    surname: String,
    age: Number,
    salary: Number,
    capitalizeFirstLetter: Function,
    initialCounter: Number,
    size: String,
  },

  data() {
    return {
      // Однонаправленный поток данных
      // Два случая желания изменить входной параметр:
      // Случай первый - дочерний компонент хочет использовать его как локальное свойство данных в дальнейшем
      counter: this.initialCounter
    }
  },

  methods: {},

  // Вычисляемые свойства
  computed: {
    // Однонаправленный поток данных
    // Случай второй - передаётся как необработанный параметр и преобразуется в вычисляемом свойстве с использованием входного параметра.
    normalizedSize() {
      return this.size.trim().toUpperCase();
    },
  },
}
</script>

<template>

  <h2>Компонент цикла</h2>

  <div>

    <p>Имя: {{ capitalizeFirstLetter(name) }}</p>
    <p>Фамилия: {{ surname.toUpperCase() }}</p>
    <p>Возраст: {{ age }}</p>
    <p>Зарплата: {{ salary }}</p>
    <br>
    <br>

    <!--Однонаправленный поток данных во Vue-->
    <!--Это когда родительское свойство обновляется - оно будет передаваться дочернему, но не наоборот.-->
    <p>Однонаправленный поток данных</p>
    <br>
    <p>{{ (counter + 2) }}</p>
    <p>{{ normalizedSize }}</p>

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