<script>
export default {

  name: 'Styles',

  components: {},

  data() {
    return {
      // Атрибут class
      str_class: 'active valid',
      cssClasses: 'red bg_green',

      // Объект с CSS классами
      objCssClasses: {
        active: true,
        valid: false,
      },
      objCustomCssClasses: {
        done: true,
        selected: false,
      },

      // CSS классы через data
      isActive: true,
      isValid: false,
      isDone: true,
      isSelected: false,
      isBgGreen: false,
    }
  },

  methods: {
    // Объект с CSS классами
    // Переключение выбора параграфа
    toggleObjSelected() {
      this.objCustomCssClasses.selected = !this.objCustomCssClasses.selected;
    },

    // Реактивность объекта с CSS классами
    // Переключение выполнения
    toggleObjDone() {
      this.objCustomCssClasses.done = !this.objCustomCssClasses.done;
    },
  },

  computed: {},

}
</script>

<template>

  <h2>Стили</h2>

  <div>

    <!--Стилизация компонента во Vue-->

    <p>Стилизация компонента</p>

    <p class="red">Красный цвет</p>
    <p class="green">Зелёный цвет</p>

    <br>
    <br>

    <!--Атрибут class во Vue-->

    <p>Атрибут class</p>

    <!--Работа с атрибутом class происходит через директиву v-bind или ее сокращенную форму ":"-->

    <p v-bind:class="str_class">Атрибут class в теге</p>
    <p :class="str_class">Атрибут class в теге</p>
    <br>
    <p v-bind:class="cssClasses">Пользовательский класс</p>
    <p :class="cssClasses">Пользовательский класс</p>

    <br>
    <br>

    <!--Объект с CSS классами во Vue-->

    <p>Объект с CSS классами</p>

    <p :class="objCssClasses">Текст с объектом стилей</p>
    <br>

    <p>
      <button type="submit" @click="toggleObjSelected">Переключить выбор параграфа</button>
    </p>
    <p :class="objCustomCssClasses">Текст с пользовательским объектом стилей</p>

    <br>
    <br>

    <!--Реактивность объекта с CSS классами во Vue-->

    <p>Реактивность объекта с CSS классами</p>

    <p>
      <button @click="toggleObjDone">Переключить выполнение параграфа</button>
    </p>
    <p :class="objCustomCssClasses">Реактивность объекта с CSS классами</p>

    <br>
    <br>

    <!--Ин лайн объект с CSS классами во Vue-->

    <p>Ин лайн объект с CSS классами</p>

    <p :class="{active: true, 'selected': true, 'has-error': false}">
      Ин лайн параграф.
    </p>
    <p :class="{active: false, 'valid': true}">
      Ин лайн параграф.
    </p>

    <br>
    <br>

    <!--CSS классы через data во Vue-->

    <p>CSS классы через data</p>
    <br>

    <p :class="{active: isActive, 'valid': isValid, 'done': isDone, 'selected': isSelected, 'bg_green': isBgGreen}">
      Параграф через data.
    </p>

    <br>
    <br>

    <!--Стилизация через атрибут style во Vue-->

    <p>Стилизация через атрибут style</p>
    <br>

    <p :style="{background: 'hsla(160, 100%, 37%, 1)', color: '#fff', fontSize: '15px', border: '3px solid #f00', fontFamily: 'bolder'}">
      Параграф через атрибут style.
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

.red, .selected {
  color: #f00;
}

.bg_green {
  background: hsla(160, 100%, 37%, 1);
  transition: 2.4s;
}

.active {
  text-decoration: underline;
}

.valid {
  color: hsla(160, 100%, 37%, 1);
  transition: 2.4s;
}

.done {
  text-decoration: line-through;
}
</style>