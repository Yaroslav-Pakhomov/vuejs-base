<script>
export default {
  name: 'WorkComponent',

  // испускаемое событие в настройке emits
  emits: ['show', "action1", 'action2', 'funcArgParent', 'workersDataParent'],

  props: {
    initialCounter: Number,
    size: String,
  },

  data() {
    return {
      // Однонаправленный поток данных
      // Два случая желания изменить входной параметр:
      // Случай первый - дочерний компонент хочет использовать его как локальное свойство данных в дальнейшем
      counter: this.initialCounter,

      // Испускаемые события с аргументами/параметрами
      work_name: '',
      work_salary: 0,
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

    // Испускаемые события
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

    // Испускаемые события с аргументами/параметрами
    // аргументы передаются после названия функции (испускаемые события)
    funcArg() {
      this.$emit('funcArgParent', 'Аргумент 1', 'Аргумент 2');
    },
    setWorkersData() {
      this.$emit('workersDataParent', this.work_name, this.work_salary);
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
    <br>

    <!--Испускаемые события с аргументами/параметрами во Vue-->
    <p>Испускаемые события с аргументами/параметрами</p>
    <br>
    <p>
      <button type="submit" @click="funcArg">Родительское событие с аргументами</button>
    </p>
    <br>
    <br>
    <p>
      <label for="work_name">Введите имя: </label>
      <input type="text" name="work_name" id="work_name" v-model="work_name">
      <br>
      <label for="work_salary">Введите зарплату: </label>
      <input type="text" name="work_salary" id="work_salary" v-model="work_salary">
      <br>
      <br>
      <button type="submit" @click="setWorkersData">Добавить работника</button>
    </p>
    <br>
    <p>Испускаемые события с аргументами/параметрами в атрибуте</p>
    <p>
      <button type="submit" @click="$emit('workersDataParent', work_name, work_salary)">Добавить работника (в
        атрибуте)
      </button>
    </p>


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