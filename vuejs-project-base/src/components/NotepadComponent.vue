<script>

import SearchNoteComponent from "@/components/SearchNoteComponent.vue";

export default {

  // Название компонента
  name: 'NotepadComponent',

  // Подключаемые компоненты
  components: {
    SearchNoteComponent,
  },

  // Свойства компонента
  data() {
    return {
      // Записи
      notes: [
        {
          id: 1,
          title: 'Заголовок записи 1',
          content: 'Содержание записи 1',
        },
        {
          id: 2,
          title: 'Заголовок записи 2',
          content: 'Содержание записи 2',
        },
        {
          id: 3,
          title: 'Заголовок записи 3',
          content: 'Содержание записи 3',
        },
        {
          id: 4,
          title: 'Заголовок записи 4',
          content: 'Содержание записи 4',
        },
      ],
      content_textarea: '',
      id_note_button: '',
    }
  },

  // Методы компонента
  methods: {

    // Помещение текста записи в textarea
    putContentTextarea(id) {
      this.notes = this.notes.map((note) => {
        if (note.id === id) {
          this.content_textarea = note.content;
          this.id_note_button = id;
        }

        return note;
      });
    },

    // Сохранение отредактированного содержания записи
    saveNoteContent(id) {
      this.notes = this.notes.map((note) => {
        if (note.id === id) {
          note.content = this.content_textarea;
        }

        return note;
      });
    },

    // Удаление выбранной записи
    deleteNoteContent(id) {
      console.log(id);
      this.notes = this.notes.filter((note) => {
        return note.id !== id;
      });
    }
  },

  // Вычисленные свойства компонента
  computed: {},

}

</script>

<template>

  <h2>Проект Блокнот</h2>
  <br>

  <SearchNoteComponent
      :notes="notes"
  />

  <div class="notepad">

    <div>
      <div v-for='note in notes' :key='note.id'>
        <a href="#" @click.prevent='putContentTextarea(note.id)'> {{ note.title }} </a>
        <button type="submit" @click.prevent='deleteNoteContent(note.id)'>X</button>
        <br>
      </div>
    </div>

    <div>
      <textarea class='notepad_content' cols='45' rows='15' v-model='content_textarea'/>
      <br>
      <input type="submit" @click.prevent='saveNoteContent(id_note_button)' value="Сохранить"
             v-bind:data-note-id='id_note_button' @input.prevent=''>
    </div>


  </div>


</template>

<style scoped>

h2 {
  text-align: center;
}

p {
  text-align: center;
}

.notepad {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-around;
}


</style>