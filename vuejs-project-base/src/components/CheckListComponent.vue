<script>

import AddItemListComponent from "@/components/AddItemListComponent.vue";
import ItemListComponent from "@/components/ItemListComponent.vue";

export default {

  // Название компонента
  name: 'CheckListComponent',

  // Подключаемые компоненты
  components: {
    ItemListComponent,
    AddItemListComponent,
  },

  // Свойства компонента
  data() {
    return {
      var1: 'Попал',

      obj_check_list: [
        {
          id: 1,
          content: 'Сходить в магазин',
        },
        {
          id: 2,
          content: 'Прогуляться',
        },
        {
          id: 3,
          content: 'Посмотреть кино',
        },
      ],
    }
  },

  // Методы компонента
  methods: {
    addItemList(content) {
      let id = this.obj_check_list.length + 1;

      this.obj_check_list.push({
            id, content
          },
      );
    },

    changeItemList(id, content) {
      this.obj_check_list = this.obj_check_list.map((item) => {
        if (item.id === id) {
          item.content = content;
        }

        return item;
      });
    },

    deleteItemList(id) {
      this.obj_check_list = this.obj_check_list.filter((item) => {
        return item.id !== id;
      });
    },
  },

  // Вычисленные свойства компонента
  computed: {},

}

</script>

<template>

  <h2>Проект Чек-лист</h2>

  <div>


    <AddItemListComponent
        @addItem='addItemList'
    />

    <br>

    <ul>
      <ItemListComponent
          v-for="item_list in obj_check_list"

          :item_id=item_list.id
          :item_content=item_list.content

          @changeItem=changeItemList
          @deleteItem=deleteItemList

          :key=item_list.id
      />


    </ul>

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