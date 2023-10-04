<script>
export default {
  name: 'Form',

  data() {
    return {
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
        {id: 1, name: 'name1', surname: 'surname1', isEdit: false,},
        {id: 2, name: 'name2', surname: 'surname2', isEdit: false,},
        {id: 3, name: 'name3', surname: 'surname3', isEdit: false,},
      ],

      form_data_users: [
        {id: 1, name: 'name1', salary: 100, age: 30, isEdit: false,},
        {id: 2, name: 'name2', salary: 200, age: 40, isEdit: false,},
        {id: 3, name: 'name3', salary: 300, age: 50, isEdit: false,},
      ],
    }
  },

  methods: {

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

    // Редактирование эл-та объекта по его ID из объекта form_users
    editUser(user) {
      user.isEdit = true;
    },

    // Сохранение эл-та объекта по его ID из объекта form_users
    saveUser(user) {
      user.isEdit = false;
    },
  },

  computed: {
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

  <h2>Форма</h2>

  <div>

    <!--Двусторонняя привязка данных к инпутам во Vue-->

    <p>Двусторонняя привязка данных к инпутам</p>

    <!-- Директива v-model - связывает свойство и инпут таким образом, чтобы изменение любого из них приводило к изменению другого-->
    <p>
      <input v-model="bind_property">
    </p>
    <p>{{ bind_property.toUpperCase() }}</p>

    <br>
    <br>

    <!--Получение данных формы по событию во Vue-->

    <p>Получение данных формы по событию</p>
    <br>

    <p>{{ form_calculate_property }}</p>

    <div>
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
      </p>
      <br>
      <br>
      <br>

      <p>
        <label>
          ФИО:
          <input v-model="form_fio_property">
        </label>
        <br>
        <button type="submit" @click="getFioSeparate">Разделить ФИО</button>
      </p>

      <p>{{ form_surname_property }}</p>
      <p>{{ form_name_property }}</p>
      <p>{{ form_patronymic_property }}</p>


    </div>

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
        <template v-if="!user.isEdit">

          Имя: {{ user.name }}, Фамилия: {{ user.surname }}
          <button type="submit" @click="editUser(user)">Редактировать</button>
          <button type="submit" @click="removeFormUser(user.id)">Х</button>

        </template>

        <!--Форма для редактирования массива объектов во Vue-->
        <template v-else>

          <p>Форма для редактирования массива объектов</p>
          <input v-model="user.name">
          <input v-model="user.surname">
          <button type="submit" @click="saveUser(user)">Сохранить</button>

        </template>
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

        <template v-if="!user.isEdit">

          <td>{{ user.name }}</td>
          <td>{{ user.age }}</td>
          <td>{{ user.salary }}</td>
          <td>
            <button type="submit" @click="editUser(user)">Редактировать</button>
            <br>
            <button type="submit" @click="removeTableUser(user.id)">Х</button>
          </td>

        </template>

        <!--Форма для редактирования массива объектов во Vue-->
        <template v-else>

          <td><input v-model="user.name"></td>
          <td><input v-model="user.age"></td>
          <td><input v-model="user.salary"></td>
          <td>
            <button type="submit" @click="saveUser(user)">Сохранить</button>
            <br>
            - Форма для редактирования
          </td>

        </template>
      </tr>
    </table>


  </div>

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