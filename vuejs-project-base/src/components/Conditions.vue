<script>

export default {
  name: 'Conditions',

  components: {},

  data() {
    return {
      // Показ по условию
      visible: true,
      invisible: false,
      visible_react: true,
      visible_toggle: true,
      visible_toggle1: true,

      isAuth: true,
      isPar: true,

      num: 2,

      age: 25,
    }
  },

  methods: {
    // Условия. Реактивное условие
    showHideText() {
      // тогглинг(переключатель) элементов
      this.visible = !this.visible;
    },
    showHideTextReact() {
      // тогглинг(переключатель) элементов
      this.visible_react = !this.visible_react;
    },
    showHideTextToggle() {
      // тогглинг(переключатель) элементов
      this.visible_toggle = !this.visible_toggle;
    },
    showHideTextToggle1() {
      // тогглинг(переключатель) элементов
      this.visible_toggle1 = !this.visible_toggle1;
    },
    toggleIsPar() {
      this.isPar = !this.isPar;
    },
  },

  computed: {},
}

</script>

<template>
  <h2>Условия</h2>

  <div>

    <!--Показ по условию-->
    <p>Показ по условию</p>
    <p v-if="visible">Показ текста visible</p>
    <!--Инвертирование-->
    <p>Инвертирование</p>
    <p v-if="!invisible">Показ текста invisible</p>

    <p>
      <button type="submit" @click="showHideText()">Показать\Скрыть текст</button>
    </p>
    <br>
    <br>


    <!--Реактивное условие, тогглинг(переключатель) элементов-->
    <p>Реактивное условие, тогглинг(переключатель) элементов</p>
    <p>
      <button type="submit" @click="showHideTextReact()" v-if="visible_react">Скрыть текст</button>
      <button type="submit" @click="showHideTextReact()" v-if="!visible_react">Показать текст</button>
      <!--<button type="submit" @click="showHideTextReact()"  v-else>Показать текст</button>-->
    </p>
    <p v-if="visible_react">Visible</p>
    <br>
    <br>

    <!--Смена текста при тогглинге(переключении) во Vue-->
    <p>Смена текста при тогглинге(переключении)</p>
    <p>
      <button type="submit" @click="showHideTextToggle()">Переключить параграф</button>
    </p>
    <p>
      {{ visible_toggle ? 'Видимый' : 'Невидимый' }} параграф 1
    </p>
    <br>
    <p>
      <button type="submit" @click="showHideTextToggle1()">Переключить параграф</button>
    </p>
    <p>
      {{ visible_toggle1 ? 'Видимый' : 'Невидимый' }} параграф 2
    </p>
    <br>
    <br>

    <!--Директива v-else во Vue-->

    <p>Директива v-else</p>
    <p v-if="isAuth">Auth</p>
    <p v-else>Not Auth</p>
    <br>
    <br>

    <!--Сложные условия во Vue-->

    <p>Сложные условия</p>
    <p v-if="num === 1 || num === 2">
      Переменная num равна одному или двум
    </p>

    <br>
    <br>

    <!--директива v-else-if во Vue-->

    <p>Директива v-else-if</p>
    <p v-if="num === 1">
      Переменная num равна одному
    </p>
    <p v-else-if="num === 2">
      Переменная num равна двум
    </p>
    <p v-else>
      Переменная num равна трём
    </p>

    <br>
    <br>

    <p v-if="age < 18">Подросток </p>
    <p v-else-if="18 <= age && age <= 25">Молодой человек</p>
    <p v-else>Мужчина</p>

    <br>
    <br>

    <!--Условные группы во Vue-->

    <p>Условные группы</p>
    <p>
      <button type="submit" @click="toggleIsPar">Показать/Скрыть параграфы</button>
    </p>
    <!--div попадает в итоговую вёрстку-->
    <div v-if="isPar">
      <p>+++</p>
      <p>+++</p>
      <p>+++</p>
    </div>
    <br>
    <br>
    <!--template не попадает в итоговую вёрстку-->
    <template v-if="isPar">
      <p>+++</p>
      <p>+++</p>
      <p>+++</p>
    </template>

    <br>
    <br>

    <!--Директива v-show во Vue-->

    <p>Директива v-show</p>
    <!--Отличия от v-if в том, что элемент с v-show будет всегда отрисовываться и оставаться в DOM, а переключаться будет лишь его CSS свойство display.
    В целом, у v-if выше затраты на переключение, в то время как v-show имеет больше затрат на первичную отрисовку. Так что используйте v-show, если переключения будут частыми, и предпочитайте v-if, если условие может и не измениться во время исполнения.
    Директиву v-show нельзя использовать на элементе template и она не работает с v-else.-->
    <p v-show="isPar">
      +++
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

img {
  width: 100%;
  margin: 5px;
  padding: 5px;
}

div ul li {
  text-align: left;
}

button {
  color: #f00;
}

table {
  margin: 0 auto;
}

table,
table th,
table td {
  border: 1px solid;
  text-align: center;
}

</style>