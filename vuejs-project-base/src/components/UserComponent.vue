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
  emits: ['removeUser', 'changeUser'],

  data() {
    return {
      isEdit: false,
      // начальные значения берутся из пропсов
      new_name: this.name,
      new_surname: this.surname,
    }
  },

  methods: {
    edit() {
      this.isEdit = true;
    },

    saveUser() {
      this.isEdit = false;
      this.$emit('changeUser', this.id, this.new_name, this.new_surname);
    }
  },

}

</script>

<template>

  <h2>Пользовательский компонент</h2>

  <div>

    <!--Реактивное удаление компонентов во Vue-->
    <!--Реактивное редактирование данных компонентов во Vue-->

    <template v-if="!isEdit">
      <p>{{ name }}</p>
      <p>{{ surname }}</p>
      <p>Реактивное редактирование данных компонентов</p>
      <p>
        <button type="submit" @click="edit()">Редактировать</button>
      </p>
      <p>Реактивное удаление компонентов</p>
      <p>
        <button type="submit" @click="$emit('removeUser', id)">Удалить</button>
      </p>
    </template>
    <template v-else>
      <p>
        <input type="text" v-model="new_name">
        <br>
        <input type="text" v-model="new_surname">
        <br>
        <button type="submit" @click="saveUser()">Сохранить</button>
      </p>
    </template>

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