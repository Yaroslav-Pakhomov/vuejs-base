<script>

export default {
  name: 'UserComponent',

  // Свойства от родительского компонента
  props: {
    id: Number,
    name: String,
    surname: String,
  },

  // Методы от родительского компонента
  emits: ['removeUser'],

}

</script>

<template>

  <h2>Пользовательский компонент</h2>


  <div>

    <!--Реактивное удаление компонентов во Vue-->
    <p>Реактивное удаление компонентов</p>

    <p>{{ name }}</p>
    <p>{{ surname }}</p>
    <p>
      <button type="submit" @click="$emit('removeUser', id)">Удалить</button>

    </p>

  </div>
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