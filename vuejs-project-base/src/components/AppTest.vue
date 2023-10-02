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

      // Циклы
      items: ['a', 'b', 'c'],
      obj_items: {a: 1, b: 2, c: 3},
      users: {user1: '100$', user2: '200$', user3: '300$',},

      // Перебор массива объектов
      users_objs: [
        {name: 'name1', surname: 'surname1',},
        {name: 'name2', surname: 'surname2',},
        {name: 'name3', surname: 'surname3',},
      ],
      hrefs: [
        {href: '1.html', text: 'text1'},
        {href: '2.html', text: 'text2'},
        {href: '3.html', text: 'text3'},
      ],
      products: [
        {name: 'product1', price: 100, quantity: 5},
        {name: 'product2', price: 200, quantity: 4},
        {name: 'product3', price: 300, quantity: 3},
      ],

      // Условия в циклах
      arr_items: [1, -2, 3, -4, 5],

      // Атрибут key
      ids_users: [
        {id: 1, name: 'name1', surname: 'surname1',},
        {id: 2, name: 'name2', surname: 'surname2',},
        {id: 3, name: 'name3', surname: 'surname3',},
      ],

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

      // Двусторонняя привязка данных к инпутам
      bind_property: 'св-во привязки',

      // Получение данных формы по событию
      form_property: 0,
      form_property2: 0,
      form_calculate_property: 0,
      form_fio_property: '',
      form_surname_property: '',
      form_name_property: '',
      form_patronymic_property: '',

      // Работа с textarea
      form_textarea_property: 'Текст по умолчанию',
      form_textarea_arr_words: [],

      // Работа с чекбоксами
      form_checkbox_property: true,

      // Работа с радио кнопками
      form_choice_radio: '',
      rus: 'rus',
      due: 'due',
      nor: 'nor',

      // Работа с выпадающими списками/селектами
      select_options: ['value1', 'value2', 'value3'],
      selected: 'value2',

      current_date: new Date(),
      selected_day: this.selectedDay(),
      selected_month: this.selectedMonth(),
      selected_year: this.selectedYear(),

      // Блокировка элементов
      isDisabled: true,

      // Модификаторы клавиш
      on_input_enter: '',
      on_click_ctrl_left: false,
      type_mouse_click: '',

      // Форма для добавления элементов массива
      form_items: ['a', 'b', 'c', 'd', 'e'],
      form_new_item: '',

      // Кнопка для удаления из массива объектов
      form_users: [
        {id: 1, name: 'name1', surname: 'surname1',},
        {id: 2, name: 'name2', surname: 'surname2',},
        {id: 3, name: 'name3', surname: 'surname3',},
      ],

      form_data_users: [
        {id: 1, name: 'name1', salary: 100, age: 30,},
        {id: 2, name: 'name2', salary: 200, age: 40,},
        {id: 3, name: 'name3', salary: 300, age: 50,},
      ],
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

    // Реактивность массивов
    // Добавить элемент
    addItemToArr() {
      this.items.push('XXX');
    },
    // Удалить 1-ый элемент - arr.splice(0, 1);
    deleteFirstItemInArr() {
      this.items.splice(0, 1);
    },
    // Удалить 2-ой элемент - arr.splice(1, 1);
    deleteSecondItemInArr() {
      this.items.splice(1, 1);
    },
    // Удалить последний элемент - arr.splice(arr[arr.length - 1], 1);
    deleteLastItemInArr() {
      let length_arr = +this.items.length;
      this.items.splice(length_arr - 1, 1);
    },
    // Удалить предпоследний элемент - arr.splice(arr[arr.length - 2], 1);
    deletePenultimateItemInArr() {
      let length_arr = +this.items.length;
      this.items.splice(length_arr - 2, 1);
    },
    // Изменить порядок элементов в arr на обратный - arr.reverse();
    reverseOrderItemInArr() {
      this.items.reverse();
    },
    // Сортировка arr в алфавитном порядке - arr.sort( (a, b) => a.localeCompare(b) );
    sortAlphabetOrderItemInArr() {
      this.items.sort((a, b) => a.localeCompare(b));
    },

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

    // Получение данных формы по событию
    // Вычисление квадрата
    getSquareNumber() {
      this.form_calculate_property = this.form_property ** 2;
    },

    // Вычисление корня квадратного
    getRootNumber() {
      this.form_calculate_property = this.form_property ** (1 / 2);
    },

    // Вычисление суммы чисел
    getSumNumbers() {
      this.form_calculate_property = (+this.form_property) + (+this.form_property2);
    },

    // Меняем числа местами
    getReverseNumbers() {
      let middle_number = this.form_property;

      this.form_property = this.form_property2;
      this.form_property2 = middle_number;
    },

    // Разделяем ФИО отдельно
    getFioSeparate() {
      let arr_fio = this.form_fio_property.split(' ');

      this.form_surname_property = arr_fio[0];
      this.form_name_property = arr_fio[1];
      this.form_patronymic_property = arr_fio[2];
    },

    // Разделяем ФИО отдельно
    getArrayWords() {
      this.form_textarea_arr_words = this.form_textarea_property.trim().split(' ');
    },

    // Работа с выпадающими списками/селектами, формирование селекта в цикле
    // Кол-во дней в выбранном месяце
    daysInMonth(month, year) {
      return new Date(year, month, 0).getDate();
    },

    // Текущий день
    selectedDay() {
      return (new Date()).getDate();
    },
    // Текущий месяц
    selectedMonth() {
      let month = +(new Date()).getMonth();
      month++;
      return month;
    },
    // Текущий год
    selectedYear() {
      return (new Date()).getFullYear();
    },

    // ...this.range(1, 12) - вызов, получение массива чисел в нужном диапазоне
    * range(start, end) {
      yield start;

      // если начальное и конечное значение совпадают
      if (start === end) return;

      // рекурсивно вызываем функцию-генератор
      yield* this.range(start + 1, end);
    },

    // Блокировка элементов
    changeDisabled() {
      this.isDisabled = !this.isDisabled;
    },

    // Модификаторы клавиш
    // Нажатие 'Enter'
    onInputEnter(event) {
      this.on_input_enter = event.target.value;
    },

    // Нажатие 'Ctrl' + лев.кн.м.
    onClickCtrlLeft() {
      this.on_click_ctrl_left = !this.on_click_ctrl_left;
    },

    // Клик лев.кн.мыши
    onClickLeft() {
      this.type_mouse_click = 'Левая кн.мыши';
    },

    // Клик пр.кн.мыши
    onClickRight() {
      this.type_mouse_click = 'Правая кн.мыши';
    },

    // Клик ср.кн.мыши
    onClickMiddle(event) {
      event.preventDefault();
      this.type_mouse_click = 'Средняя кн.мыши';
    },

    // Форма для добавления элементов массива
    // Добавление элемента в конец массива
    addEndFormNewItem() {
      this.form_items.push(this.form_new_item);
    },
    // Добавление элемента в конец массива
    addStartFormNewItem() {
      this.form_items.unshift(this.form_new_item);
    },

    // Кнопка для удаления элемента массива
    // Удаление эл-та по его индексу
    removeFormItem(index) {
      this.form_items.splice(index, 1);
    },

    // Кнопка для удаления из массива объектов
    // Удаление эл-та объекта по его ID из объекта form_users
    removeFormUser(id) {
      this.form_users = this.form_users.filter(function (user) {
        return user.id !== id;
      });
    },

    // Удаление эл-та объекта по его ID из объекта form_data_users
    removeTableUser(id) {
      this.form_data_users = this.form_data_users.filter(function (user) {
        return user.id !== id;
      });
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

    // Работа с выпадающими списками/селектами
    // Кол-во дней в текущем месяце для выпадающего списка
    select_days() {
      let number_days = this.daysInMonth(this.selected_month, this.selected_year);
      return [...this.range(1, number_days)];
    },

    // Кол-во месяцев для выпадающего списка
    select_months() {
      return [...this.range(1, 12)];
    },

    // Кол-во лет для выпадающего списка
    select_years() {
      return [...this.range(1945, 2030)];
    },

    // День недели
    weekDay() {
      let month = this.selected_month;
      month--;
      return this.getWeekDay(this.selected_day, month, this.selected_year);
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

    <!-- Модификаторы событий во Vue. -->

    <p>

      Модификаторы событий во Vue.
      <br>
      <br>


      <a href="https://ya.ru" target="_blank" @click.prevent>Яндекс</a>
      <br>
      <button type="submit" @click.once="increaseCost()">Увеличить цену(+100) один раз</button>
      <button type="submit" @click.once="decreaseCost()">Уменьшить цену(-100) один раз</button>

      <br>

    </p>
    <br>
    <br>
    <br>
    <br>
    <br>

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

    <h2>Циклы</h2>

    <div>

      <!--Перебор массивов во Vue-->

      <p>Перебор массивов</p>

      <p v-for="elem in items">{{ elem }}</p>
      <div v-for="elem in items">{{ elem }}</div>
      <ul>
        <li v-for="elem in items">{{ elem }}</li>
      </ul>

      <br>
      <br>

      <!--Получение ключей при переборе массивов во Vue-->

      <p>Получение ключей при переборе массивов</p>
      <ul>
        <li v-for="(elem, key) in items">{{ key + 1 }}. {{ elem }}</li>
      </ul>

      <br>
      <br>

      <!--Перебор объектов во Vue-->

      <p>Перебор объектов</p>
      <ul>
        <li v-for="(elem, key, index) in obj_items">{{ index + 1 }}. Ключ - {{ key }}, элемент - {{ elem }}</li>
      </ul>

      <br>
      <br>

      <ul>
        <li v-for="(user, name, index) in users">{{ name }} - {{ user }} - {{ index + 1 }}</li>
      </ul>

      <br>
      <br>

      <!--Перебор группы тегов во Vue-->

      <p>Перебор группы тегов</p>

      <div v-for="(elem, key) in items">
        <hr>
        <p>
          Ключ - {{ key }}, элемент - {{ elem }}
        </p>
        <hr>
        <br>
      </div>
      <br>

      <!--Объединение тегов без родителя-->
      <template v-for="(elem, key) in items">
        <hr>
        <p>
          Ключ - {{ key }}, элемент - {{ elem }}
        </p>
        <hr>
        <br>
      </template>

      <ul>
        <!--Объединение тегов без родителя-->
        <template v-for="(elem) in items">
          <li>{{ elem }}</li>
          <li class="divider">divider</li>
        </template>
      </ul>

      <br>
      <br>

      <!--Перебор массива объектов во Vue-->

      <p>Перебор массива объектов</p>
      <br>

      <p v-for="user in users_objs">
        {{ user.name }} {{ user.surname }}
      </p>
      <br>

      <ul>
        <li v-for="href in hrefs"><a :href="href.href">{{ href.text }}</a></li>
      </ul>
      <br>

      <table>
        <tr v-for="product in products">
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td>{{ product.quantity }}</td>
        </tr>
      </table>

      <br>
      <br>

      <!--Цикл в диапазоне во Vue-->

      <p>Цикл в диапазоне</p>
      <br>
      <p v-for="iter in 10">
        Номер итерации в диапазоне цикла: {{ iter }}
      </p>

      <br>
      <br>

      <!--Условия в циклах во Vue-->

      <p>Условия в циклах</p>
      <br>

      <ul>
        <template v-for="item in arr">
          <li v-if="item < 13">{{ item }}</li>
        </template>
      </ul>

      <br>

      <template v-for="item in arr_items">
        <p v-if="item >= 0">{{ item }}</p>
      </template>

      <br>
      <br>

      <!--Атрибут key во Vue-->

      <p>Атрибут key</p>
      <!--key - уникальный атрибут, который определяет идентичность каждого элемента, т.о. позволяя переиспользовать и упорядочивать существующие элементы.
      Рекомендуется всегда указывать атрибут key с v-for, кроме случаев когда итерируемое содержимое DOM простое, или когда сознательно полагаетесь на стратегию обновления по умолчанию для улучшения производительности.-->
      <br>
      <p v-for="user in ids_users" :key="user.id">
        Имя: {{ user.name }}, Фамилия: {{ user.surname }}
      </p>

      <br>
      <br>

      <!--Реактивность массивов во Vue-->

      <p>Реактивность массивов</p>

      <p>
        <button @click.prevent="addItemToArr()">Добавить элемент</button>
      </p>
      <p>
        <button @click.prevent="deleteFirstItemInArr()">Удалить 1-ый элемент</button>
      </p>
      <p>
        <button @click.prevent="deleteSecondItemInArr()">Удалить 2-ой элемент</button>
      </p>
      <p>
        <button @click.prevent="deletePenultimateItemInArr()">Удалить предпоследний элемент</button>
      </p>
      <p>
        <button @click.prevent="deleteLastItemInArr()">Удалить последний элемент</button>
      </p>
      <p>
        <button @click.prevent="reverseOrderItemInArr()">Реверс сортировка</button>
      </p>
      <p>
        <button @click.prevent="sortAlphabetOrderItemInArr()">Алфавитная сортировка</button>
      </p>

      <p v-for="item in items">
        {{ item }}
      </p>


      <br>
      <br>


    </div>
    <br>
    <br>
    <br>
    <br>
    <br>

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

    <h2>Форма</h2>

    <div>

      <!--Двусторонняя привязка данных к инпутам во Vue-->

      <p>Двусторонняя привязка данных к инпутам</p>

      <!-- Директива v-model - связывает свойство и инпут таким образом, чтобы изменение любого из них приводило к изменению другого-->
      <p>
        <input v-model="bind_property">
        <p>{{ bind_property.toUpperCase() }}</p>
      </p>

      <br>
      <br>

      <!--Получение данных формы по событию во Vue-->

      <p>Получение данных формы по событию</p>
      <br>

      <p>{{ form_calculate_property }}</p>

      <p>
        <label>
          Число 1:
          <input v-model="form_property">
        </label>
        <br>
        <label>
          Число 2:
          <input v-model="form_property2">
        </label>
        <br>
        <button type="submit" @click="getSquareNumber">Квадрат</button>
        <br>
        <button type="submit" @click="getRootNumber">Корень</button>
        <br>
        <button type="submit" @click="getSumNumbers">Сумма чисел</button>
        <br>
        <button type="submit" @click="getReverseNumbers">Реверс</button>

        <br>
        <br>
        <br>

        <label>
          ФИО:
          <input v-model="form_fio_property">
        </label>
        <br>
        <button type="submit" @click="getFioSeparate">Разделить ФИО</button>

        <p>{{ form_surname_property }}</p>
        <p>{{ form_name_property }}</p>
        <p>{{ form_patronymic_property }}</p>


      </p>

      <br>
      <br>

      <!--Работа с textarea во Vue-->

      <p>Работа с textarea</p>
      <br>

      <p>
        <textarea v-model="form_textarea_property"></textarea>
      </p>
      <br>

      <p>
        <button type="submit" @click="getArrayWords">Получить список слов</button>
      </p>
      <br>

      <p>{{ form_textarea_property }}</p>
      <br>

      <ul>
        <li v-for="word in form_textarea_arr_words">
          {{ word }}
        </li>
      </ul>

      <br>
      <br>

      <!--Работа с чекбоксами во Vue-->

      <p>Работа с чекбоксами</p>
      <br>

      <p>
        <label>
          Чекбокс
          <input type="checkbox" v-model="form_checkbox_property">
        </label>
      </p>
      <p>{{ form_checkbox_property }}</p>
      <p>{{ form_checkbox_property ? 'yes' : 'no' }}</p>
      <p v-if="form_checkbox_property">Скрытый параграф</p>

      <br>
      <br>

      <!--Работа с радио кнопками во Vue-->

      <p>Работа с радио кнопками</p>
      <br>

      <p>
        Язык
        <br>

        <label>
          Русский
          <input type="radio" v-model="form_choice_radio" value="rus">
        </label>
        <br>
        <label>
          Германский
          <input type="radio" v-model="form_choice_radio" value="due">
        </label>
        <br>
        <label>
          Норвежский
          <input type="radio" v-model="form_choice_radio" value="nor">
        </label>
      </p>
      <br>

      <p>Ваш выбор: {{ form_choice_radio }}</p>

      <p v-if="form_choice_radio === rus">Россия превыше всего</p>
      <p v-if="form_choice_radio === due">Deutschland über allen</p>
      <p v-if="form_choice_radio === nor">Norge først og fremst</p>

      <br>
      <br>

      <!--Работа с выпадающими списками/селектами во Vue-->

      <p>Работа с выпадающими списками/селектами</p>
      <br>

      <p>
        <select v-model="selected">
          <option v-for="select_option in select_options">{{ select_option }}</option>
        </select>
      </p>
      <br>

      <p>Выбранный пункт: {{ selected }}</p>

      <br>
      <p>
        Дата
        <br>
        Число:
        <select v-model="selected_day">
          <option v-for="select_day in select_days">{{ select_day }}</option>
        </select>
        Месяц:
        <select v-model="selected_month">
          <option v-for="select_month in select_months">{{ select_month }}</option>
        </select>
        Год:
        <select v-model="selected_year">
          <option v-for="select_year in select_years">{{ select_year }}</option>
        </select>
      </p>

      <p>
        {{ selected_day > 9 ? selected_day : '0' + selected_day }}
        . {{ selected_month > 9 ? selected_month : '0' + selected_month }}
        . {{ selected_year }}
      </p>
      <p>{{ weekDay }}</p>

      <br>
      <br>

      <!--Блокировка элементов во Vue-->

      <p>Блокировка элементов</p>
      <br>

      <p>
        <input type="text" v-bind:disabled="isDisabled">
        <br>
        <button type="submit" @click="changeDisabled">Изменить доступность</button>
        <br>
        <label>
          Вкл/выкл доступность
          <input type="checkbox" v-model="isDisabled">
        </label>
      </p>

      <br>
      <br>

      <!--Модификаторы клавиш во Vue-->

      <p>Модификаторы клавиш</p>
      <br>

      <!--Нажатие 'Enter'-->
      <p>
        Нажатие 'Enter'
        <input type="text" @keyup.enter="onInputEnter">
      </p>
      <p>{{ on_input_enter }}</p>
      <br>

      <!--Нажатие 'Ctrl' + лев.кн.м.-->
      <p>
        Нажатие 'Ctrl' + лев.кн.м.
        <a href="#" @click.ctrl.left.exact.prevent="onClickCtrlLeft">Ссылка абзаца</a>
      </p>
      <p v-if="on_click_ctrl_left">Текст модификатора клавиш</p>
      <br>

      <!--Клик лев.кн.мыши, Клик пр.кн.мыши, Клик ср.кн.мыши-->
      <p>
        Клик лев.кн.мыши,
        Клик пр.кн.мыши,
        Клик ср.кн.мыши
        <br>
        <a href="#" @click.left.exact.prevent="onClickLeft" @click.right.exact.prevent="onClickRight"
           @click.middle.exact.prevent="onClickMiddle">Ссылка абзаца</a>
      </p>
      <p>"{{ type_mouse_click }}"</p>

      <br>
      <br>

      <!--Форма для добавления элементов массива во Vue-->

      <p>Форма для добавления элементов массива</p>
      <br>

      <p>
        <button type="submit" @click="addStartFormNewItem">Добавить элемент в начало</button>
        <button type="submit" @click="addEndFormNewItem">Добавить элемент в конец</button>
        <br>
        <input type="text" v-model="form_new_item">
      </p>

      <ul>
        <li v-for="(item, index) in form_items" :key="index">
          <span @click="removeFormItem(index)">{{ index }} - {{ item }} </span>
          <!--Кнопка для удаления элемента массива-->
          <button type="submit" @click="removeFormItem(index)">Х</button>
        </li>
      </ul>

      <br>
      <br>

      <!--Кнопка для удаления из массива объектов во Vue-->

      <p>Кнопка для удаления из массива объектов</p>
      <br>

      <ul>
        <li v-for="(user) in form_users" :key="user.id">
          Имя: {{ user.name }}, Фамилия: {{ user.surname }}
          <button type="submit" @click="removeFormUser(user.id)">Х</button>
        </li>
      </ul>
      <br>

      <table>
        <tr>
          <th>Имя</th>
          <th>Зарплата</th>
          <th>Возраст</th>
          <th>Действие</th>
        </tr>
        <tr v-for="user in form_data_users" :key="user.id">
          <td>{{ user.name }}</td>
          <td>{{ user.age }}</td>
          <td>{{ user.salary }}</td>
          <td>
            <button type="submit" @click="removeTableUser(user.id)">Х</button>
          </td>
        </tr>
      </table>


    </div>

    <br>
    <br>
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
//display: none;
}
</style>