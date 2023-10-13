<script>

export default {
  name: 'AddUserComponent',

  // Свойства от родительского компонента
  props: {},

  // Методы от родительского компонента
  emits: ['addUser'],

  // Свойства компонента
  data() {
    return {
      add_user_name: '',
      add_user_surname: '',
    }
  },

  // Методы компонента
  methods: {
    save() {
      this.$emit('addUser', this.add_user_name, this.add_user_surname);
    },
  },

  // Вычисляемые свойства компонента
  computed: {}
}

</script>

<template>

  <h2>Компонент добавления пользователей</h2>

  <div>

    <p>Форма добавления пользователя</p>

    <form action="#">
      <p>
        <label>
          Введите имя пользователя
          <input type="text" id="add_name" v-model="add_user_name">
        </label>
      </p>
      <p>
        <label>
          Введите фамилию пользователя
          <input type="text" id="add_surname" v-model="add_user_surname">
        </label>
      </p>
      <p>
        <button type="submit" @click.prevent="save()">Добавить пользователя</button>
      </p>

    </form>

  </div>

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