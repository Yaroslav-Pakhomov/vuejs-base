<script>
export default {
  name: 'AppTest',

  // Переменные
  data() {
    return {
      name: 'John',
      surname: 'Smith',

      attr_src: './img/img1.jpg',
      attr_alt: 'img',

      a_text: 'Ссылка страницы',
      a_href: 'page.html',

      var1: 12,
      var2: 13,

      arr: [11, 12, 13],

      obj: {a: 111, b: 112, c: 113},

      objs_arr: [
        {volume: 'Малый', price: 100},
        {volume: 'Средний', price: 200},
        {volume: 'Большой', price: 300},
      ],

      text_par_bool: true,
      text_par: 'Текст по умолчанию.',

      text_par_mouseover_bool: true,
      text_par_mouseover: 'Текст наведения по умолчанию.',

      text_method: 'Текст для метода',

      text_react: 'Текст для реактивности',

      // Вычисляемые свойства
      cost: 1100,
      amount: 3,

    }
  },

  // Методы
  methods: {
    // Через замыкание
    showLink: function () {
      return 'Текст ссылки: "' + this.a_text + '", адрес ссылки: "' + this.a_href + '".';
    },

    // Через объявление
    showImg() {
      return 'Текст описания: "' + this.attr_alt + '", адрес изображения: "' + this.attr_src + '".';
    },

    // Текущая дата
    currentDate() {
      let date = new Date();
      return (date.getFullYear() + '-' + date.getMonth() + '-' + date.getDate());
    },

    // Текст параграфа при клике
    setTextPar() {
      this.text_par_bool = !this.text_par_bool;
      return this.text_par = this.text_par_bool ? 'Текст по умолчанию.' : 'Текст параграфа изменение.';
    },

    // Текст параграфа при наведении
    setTextParMouseover() {
      this.text_par_mouseover_bool = !this.text_par_mouseover_bool;
      return this.text_par_mouseover = this.text_par_mouseover_bool ? 'Текст наведения по умолчанию.' : 'Текст наведения на параграфа изменение.';
    },

    // Сумма эл-тов массива
    getArrSum() {
      let summa = 0;

      for (let elem of this.arr) {
        summa += (+elem);
      }

      return summa;
    },

    // Метод и вспомогательный метод
    showTextPar() {
      return this.capitalLetter(this.text_method);
    },
    // Метод делает заглавной первую букву переданной строки
    capitalLetter(str) {
      return str[0].toUpperCase() + str.slice(1);
    },

    getFullDate(date = 0, month = 0, year = 0) {
      // текущая дата
      let nowDate = new Date();

      date = date ? date : nowDate.getDate();
      month = (month - 1) >= 0 ? (month - 1) : nowDate.getMonth();
      year = year ? year : nowDate.getFullYear();

      return 'День недели выбранной даты: ' + this.getWeekDay(date, month, year);
    },

    // Вспомогательный метод принимает дату в виде строки, возвращает день недели
    getWeekDay(date, month, year) {
      let selectDate = '';
      let week = ['вс', 'пн', 'вт', 'ср', 'чт', 'пт', 'сб',];

      selectDate = new Date(year, month, date);
      let selectDay = week[selectDate.getDay()];

      month++;
      month = month >= 10 ? month : '0' + month;
      date = date >= 10 ? date : '0' + date;

      return selectDay + ' - ' + date + '.' + month + '.' + year;
    },

    // Передача параметром объекта события
    setTextBtn(event) {
      console.log(event);
      console.log(event.target);
      console.log('Содержание внутри тега: "' + event.target.innerHTML + '"');
      console.log('Значение переданное тегом: "' + event.target.value + '"');
    },

    // Реактивность данных
    setReactivityProp() {
      this.text_react = 'Изменённый реактивный текст.';
    },

    // Вычисляемые свойства
    increaseCost() {
      this.cost += 100;
    },
    decreaseCost() {
      this.cost -= 100;
    },
  },

  // Вычисляемые свойства во Vue
  computed: {
    full_name() {
      return this.name + ' ' + this.surname;
    },
    price() {
      return this.cost * this.amount;
    },
  },

}

</script>

<template>
  <div class="container">
    <h2 class="green">
      Hello, World AppTest!
    </h2>

    <!-- Переменные -->
    <p>{{ name }}</p>
    <p>{{ surname }}</p>

    <!-- Директиву "v-bind:" для работы с атрибутами. Директиву "v-bind:" можно сократить до ":". -->
    <p>
      <img v-bind:src="attr_src" :alt="attr_alt">
    </p>

    <p>
      <a :href="a_href">{{ a_text }}</a>
    </p>

    <!-- Выполнения кода в представлениях Vue. -->
    <p>
      {{ var1 + var2 }}
    </p>

    <br>

    <!-- Массивы во Vue. -->
    <p>
      Массивы во Vue.
      <br>

      <ul>
        {{ arr }}
        <li v-for="elem in arr">
          {{ elem }}
        </li>
      </ul>

    </p>

    <!-- Объекты во Vue. -->
    <p>
      Объекты во Vue.
      <br>

      {{ obj }}
      <br>

      {{ obj.a }}
      <br>

      {{ obj['b'] }}
      <br>

      {{ obj.c }}

      <ul>
        <li v-for="elem in obj">
          {{ elem }}
        </li>
      </ul>
    </p>
    <br>

    <!-- Массив объектов во Vue. -->
    <p>

      Массив объектов во Vue
      <br>
      {{ objs_arr }}
      <br>
      <br>
      <ul>
        <li v-for="(prod, index) in objs_arr">
          {{ index + 1 }}. Объём - {{ prod.volume }}, цена: {{ prod.price }} р.
        </li>
      </ul>

    </p>
    <br>
    <br>

    <!-- Работа с методами во Vue. -->

    <p>
      Работа с методами во Vue.
      <br>
      <br>

      {{ showLink() }}
      <br>
      <br>

      {{ showImg() }}
      <br>
      <br>

      {{ currentDate() }}
    </p>
    <br>
    <br>


    <!-- Навешивание обработчиков событий во Vue. -->

    <div>

      <p>
        Навешивание обработчиков событий во Vue
        <br>
        <br>

        <button v-on:click="setTextPar">
          Нажми
        </button>
      </p>
      <br>

      <p>{{ text_par }}</p>
      <br>

      <p v-on:mouseover="setTextParMouseover">{{ text_par_mouseover }}</p>

    </div>
    <br>
    <br>

    <!-- Работа с data внутри методов Vue. -->

    <p>

      Работа с data внутри методов Vue.
      <br>
      <br>

      <span>Сумма элементов списка {{ arr }}: {{ getArrSum() }}</span>

    </p>
    <br>
    <br>

    <!-- Вспомогательные методы во Vue. -->

    <p>

      Вспомогательные методы во Vue.
      <br>
      <br>

      {{ showTextPar() }}
      <br>
      {{ getFullDate() }}
      <br>
      {{ getFullDate(10) }}

    </p>
    <br>
    <br>

    <!-- Передача параметров в метод во Vue. -->

    <p>

      Передача параметров в метод во Vue.
      <br>
      <br>

      <button @click="setTextBtn($event)" value="10">Кнопка 1</button>
      <br>
      <button @click="setTextBtn($event)" value="20">Кнопка 2</button>

    </p>
    <br>
    <br>

    <!-- Реактивность во Vue. -->

    <p>

      Реактивность во Vue.
      <br>
      <br>

      {{ text_react }}
      <br>

      <button @click="setReactivityProp()" value="10">Реактивность</button>
      <br>

    </p>
    <br>
    <br>

    <!-- Вычисляемые свойства во Vue. -->

    <p>

      Вычисляемые свойства во Vue.
      <br>
      <br>

      ФИО
      <p>{{ name }}</p>
      <p>{{ surname }}</p>
      <p>{{ full_name }}</p>
      <br>

      Корзина
      <p>Цена: {{ cost }}</p>
      <p>Кол-во: {{ amount }}</p>
      <p>Стоимость: {{ price }}</p>
      <button type="submit" @click="increaseCost()">Увеличить цену(+100)</button>
      <button type="submit" @click="decreaseCost()">Уменьшить цену(-100)</button>

      <br>

    </p>
    <br>
    <br>


  </div>
</template>

<style scoped>
div.container {
  margin-top: 40px;
  margin-bottom: 40px;
}

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
</style>