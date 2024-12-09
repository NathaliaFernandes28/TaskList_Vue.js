<template>
    <div id="app">
      <Heading/>
      <Form @add-item="adicionarItem" />
      <List :items="lista" @toggle-item="alternarFeito" />
    </div>
  </template>


<script >
import "./assets/main.css"
import Form from "./components/Form.vue"
import Heading from "./components/Heading.vue";
import List from "./components/List.vue";

export default {
    components: {
        Form,
        Heading,
        List,
    },
    data() {
    return {
      lista: [],
    };
  },
  methods: {
    adicionarItem(novoItem) {
      this.lista.push(novoItem);
    },
    alternarFeito(index) {
      this.lista[index].feito = !this.lista[index].feito;
    },
  },
}

</script>


