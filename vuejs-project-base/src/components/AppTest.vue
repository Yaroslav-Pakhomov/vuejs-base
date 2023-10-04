<script>

import Base from "@/components/Base.vue";
import Conditions from "@/components/Conditions.vue";
import Cycles from "@/components/Cycles.vue";
import Styles from "@/components/Styles.vue";
import Form from "@/components/Form.vue";
import TestComponent from "@/components/TestComponent.vue";

export default {
  name: 'AppTest',

  components: {
    Base,
    Conditions,
    Cycles,
    Styles,
    Form,
    TestComponent,
  },

  // Переменные
  data() {
    return {}
  },

  // Методы
  methods: {},

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
    <TestComponent name='john' surname='smith' age='32' :arg_arr='["a", "b", "c", 1, 2, 3,]'
                   :arg_obj='{a:1 , b:2, c:3, }' :arg_bool='true'/>

  </div>
</template>

<style scoped>
div.container {
  margin-top: 40px;
  margin-bottom: 40px;
}
</style>