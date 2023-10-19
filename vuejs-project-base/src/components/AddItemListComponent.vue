<script>

export default {

  // Название компонента
  name: 'AddItemListComponent',

  // Свойства от родительского компонента
  props: {},

  // Методы от родительского компонента
  emits: ['addItem',],

  // Свойства компонента
  data() {
    return {
      add_item_list: '',
    }
  },

  // Методы компонента
  methods: {
    add() {
      this.$emit('addItem', this.add_item_list);
    }
  },

  // Вычисленные свойства компонента
  computed: {},

}

</script>

<template>

  <h3>Добавить задачу</h3>
  <p>
    <input type="text" v-model="add_item_list">
    <input type="submit" @click="add" value="Добавить">
  </p>

</template>

<style scoped>

h2, h3 {
  text-align: center;
}

p {
  text-align: center;
}

button {
  color: #f00;
}

</style>