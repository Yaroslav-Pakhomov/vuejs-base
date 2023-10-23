<script>

import Base from "@/components/Base.vue";
import Conditions from "@/components/Conditions.vue";
import Cycles from "@/components/Cycles.vue";
import Styles from "@/components/Styles.vue";
import Form from "@/components/Form.vue";
import TestComponent from "@/components/TestComponent.vue";
import ArrComponent from "@/components/ArrComponent.vue";
import WorkComponent from "@/components/WorkComponent.vue";
import UserComponent from "@/components/UserComponent.vue";
import AddUserComponent from "@/components/AddUserComponent.vue";
import CheckListComponent from "@/components/CheckListComponent.vue";
import NotepadComponent from "@/components/NotepadComponent.vue";

export default {
  name: 'AppTest',

  // Подключаемые компоненты в текущий
  components: {
    UserComponent,
    Base,
    Conditions,
    Cycles,
    Styles,
    Form,
    TestComponent,
    ArrComponent,
    WorkComponent,
    AddUserComponent,
    CheckListComponent,
    NotepadComponent,
  },

  // Переменные
  data() {
    return {
      parent_name: 'Tony',
      parent_surname: 'Stark',
      parent_age: 32,
      parent_salary: 2000,
      parent_arr_users: [
        {id: 1, name: 'john', surname: 'smith', age: 20, salary: 2000},
        {id: 2, name: 'tony', surname: 'stark', age: 37, salary: 200000},
        {id: 3, name: 'tony', surname: 'montana', age: 32, salary: 1000000},
      ],
      initialCounter: 0,
      size: " middle ",

      // Реактивное удаление компонентов
      users: [
        {
          id: 1,
          name: 'Иван',
          surname: 'Иванов',
        },
        {
          id: 2,
          name: 'Петр',
          surname: 'Петров',
        },
        {
          id: 3,
          name: 'Сидор',
          surname: 'Сидоров',
        },
      ],
    }
  },

  // Методы
  methods: {
    // Слово с заглавной буквы
    capitalizeFirstLetter(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    },

    // Испускаемые события
    func() {
      alert('xxx');
    },
    log1() {
      console.log('Функция 1');
    },
    log2() {
      console.log('Функция 2');
    },

    // Испускаемые события с аргументами/параметрами
    funcArg(arg1, arg2) {
      console.log(arg1 + ', ' + arg2);
    },
    workersData(name, salary) {
      console.log('Имя: ' + name + ', зарплата - ' + salary);
    },

    // Реактивное удаление компонентов
    removeElemUsers(id) {
      this.users = this.users.filter((user) => {
        return user.id !== id;
      });
    },

    // Реактивное редактирование данных компонента
    changeElemUsers(id, name, surname) {
      this.users = this.users.map((user) => {
        if (user.id === id) {
          user.name = name;
          user.surname = surname;
        }
        return user;
      });
    },

    // Реактивное добавления данных компонента
    addElemUsers(name, surname) {
      let id = this.users.length + 1;

      this.users.push({
        id, name, surname
      });
    }


  },

  // Вычисляемые свойства во Vue
  computed: {},

}

</script>

<template>
  <div class="container">

    <Base/>

    <Conditions/>

    <Cycles/>

    <Styles/>

    <Form/>

    <!--  Передача данных в дочерний компонент  -->
    <!--  Для этого нужно байндить атрибут через директиву v-bind или ее сокращенную форму ":".  -->
    <TestComponent name='john' surname='smith' age='32'
                   :arg_arr='["a", "b", "c", 1, 2, 3,]' :arg_obj='{a:1 , b:2, c:3, }' :arg_bool='true'
                   :parent_name='parent_name' :parent_surname='parent_surname'
                   :parent_age='parent_age' :parent_salary='parent_salary'/>

    <!--  Создание компонентов в цикле  -->
    <ArrComponent v-for="user in parent_arr_users" :key=user.id :name='user.name' :surname='user.surname' :age=user.age
                  :salary=user.salary :capitalizeFirstLetter='capitalizeFirstLetter'/>

    <br>
    <br>
    <br>
    <br>

    <!--Передадим метод func() параметром @show в дочерний компонент-->
    <WorkComponent :initialCounter='initialCounter' :size="size"
                   @show="func" @action1="log1" @action2="log2"
                   @funcArgParent='funcArg' @workersDataParent='workersData'/>

    <!--Реактивное удаление компонентов-->
    <!--Реактивное редактирование данных компонентов-->
    <UserComponent
        v-for="user in users"

        :id=user.id
        :name=user.name
        :surname=user.surname
        @removeUser=removeElemUsers
        @changeUser=changeElemUsers

        :key=user.id
    />

    <AddUserComponent
        @addUser=addElemUsers
    />

    <!--Чек-лист-->
    <CheckListComponent/>

    <!--Блокнот-->
    <NotepadComponent/>


    <br>
    <br>
    <br>
    <br>
    <br>

  </div>
</template>

<style scoped>
div.container {
  margin-top: 40px;
  margin-bottom: 40px;
}
</style>