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
    }
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