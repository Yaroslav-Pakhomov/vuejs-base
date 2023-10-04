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

    <TestComponent/>

  </div>
</template>

<style scoped>
div.container {
  margin-top: 40px;
  margin-bottom: 40px;
}
</style>