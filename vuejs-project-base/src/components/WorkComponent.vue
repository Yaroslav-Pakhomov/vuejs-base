<script>
export default {
  name: 'WorkComponent',

  // испускаемое событие в настройке emits
  emits: ['show', "action1", 'action2'],

  props: {
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

    // в обработчике клика заставим вызваться родительскую функцию
    // с помощью функции $emit в параметр передадим имя испускаемого события
    handle() {
      this.$emit('show');
    },
    log1() {
      this.$emit('action1');
    },
    log2() {
      this.$emit('action2');
    },
  },
}
</script>

<template>

  <h2>Рабочий компонент</h2>
  <br>
  <br>

  <div>

    <!--Однонаправленный поток данных во Vue-->
    <!--Это когда родительское свойство обновляется - оно будет передаваться дочернему, но не наоборот.-->
    <p>Однонаправленный поток данных</p>
    <br>
    <p>{{ (counter + 2) }}</p>
    <p>{{ normalizedSize }}</p>
    <br>
    <br>

    <!--Испускание событий во Vue-->
    <p>Испускание событий</p>
    <br>
    <p>
      <button type="submit" @click="handle">Кнопка alert</button>
    </p>
    <br>
    <p>
      <button type="submit" @click="log1">Кнопка LOG1</button>
    </p>
    <br>
    <p>
      <button type="submit" @click="log2">Кнопка LOG2</button>
    </p>
    <br>
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

button {
  color: #f00;
}

</style>