<script>

export default {

  // Название компонента
  name: 'SearchNoteComponent',

  // Свойства переданные от родительского компонента
  props: {
    notes: Object,
  },

  // Методы переданные от родительского компонента
  emits: {},

  // Свойства компонента
  data() {
    return {
      search_notes: [],
      search_note_value: '',
    };
  },

  // Методы компонента
  methods: {
    searchNotes() {
      console.log(this.search_note_value);

      this.search_notes = this.notes.filter((note) => {
        let str_title = note.title;
        let str_content = note.content;
        // event.target.value
        return str_content.indexOf(this.search_note_value) >= 0 || str_title.indexOf(this.search_note_value) >= 0;

      });

      console.log(this.search_notes);

    },
  },

  // Вычисляемые свойства компонента
  computed: {},

}

</script>

<template>

  <h3>Поиск по записям</h3>
  <br>

  <div class="notepad_search">
    <!--    @input.prevent='searchNotes'-->
    <input type='text' placeholder='Поиск по записям' @input.prevent='searchNotes' v-model="search_note_value">
    <input type="submit" @click.prevent='searchNotes' value="Поиск">
  </div>

  <div>

    <div v-if="search_notes.length">
      <br>
      <p>Результаты поиска:</p>

      <template v-for="search_note in search_notes" :key='search_note.id'>
        <p>Заголовок: {{ search_note.title }}</p>
        <p>Содержание: {{ search_note.content }}</p>
      </template>
    </div>

  </div>
  <br>
  <br>

</template>

<style scoped>

</style>