<script>
export default {
  name: 'Cycles',

  components: {},

  data() {
    return {

      // Циклы
      arr: [11, 12, 13],
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
    }
  },

  methods: {
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
  },

  computed: {},
}
</script>

<template>

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