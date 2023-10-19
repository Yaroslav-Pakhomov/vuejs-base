<script>

export default {

  // Название компонента
  name: 'ItemListComponent',

  // Свойства от родительского компонента
  props: {
    item_id: Number,
    item_content: String,
  },

  // Методы от родительского компонента
  emits: ['changeItem', 'deleteItem'],

  // Свойства компонента
  data() {
    return {
      content_item: this.item_content,
      isEdit: false,

      checked: false,

      styles: {
        done: false,
      }
    }
  },

  // Методы компонента
  methods: {

    // Кнопка "Редактировать" и "Сохранить"
    editItem() {
      this.isEdit = !this.isEdit;
    },

    // Кнопка 'Удалить'
    deleteItem(id) {
      this.$emit('deleteItem', id);
    },

    // Кнопка "Сохранить"
    change(id, item) {
      this.editItem();
      this.$emit('changeItem', id, item);
    },


    // Клик по пункту/чек-боксу
    doneToggleItem() {
      this.styles.done = !this.styles.done;
      this.checked = this.styles.done;
    },

  },

  // Вычисленные свойства компонента
  computed: {},

}

</script>

<template>

  <li>
    <template v-if="!isEdit">
      <input type="checkbox" @change.prevent='doneToggleItem()' :id="'item_id_' + item_id" v-model="checked">
      <label @click.prevent='doneToggleItem()' :class="styles" :for="'item_id_' + item_id">
        {{ item_content }}
      </label>
      <input type="button" @click='deleteItem(item_id)' value="Удалить">
      <input type="button" @click='editItem()' value="Редактировать">
    </template>
    <template v-else>
      <label>
        <input type="text" v-model="content_item" :key='item_id'>
      </label>
      <input type="button" @click='change(item_id, content_item)' value="Сохранить">
    </template>
  </li>

</template>

<style scoped>

.done {
  text-decoration: line-through;
}

</style>