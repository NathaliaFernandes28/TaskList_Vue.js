<template>
    <div id="form-wrapper">
   <div id="o-form">
     <input
       type="text"
       v-model="textoNovoItem"
       @keyup.enter="salvarNovoItem"
       maxlength="20"
       placeholder="Adicionar nova tarefa"
     />
     <div class="checkboxImportante">
       <input type="checkbox" v-model="novoItemImportante" id="is-importante" />
       <label for="is-importante"> Importante</label>
     </div>
     <button @click="salvarNovoItem" v-if="textoNovoItem.length > 0">
       Salvar
     </button>
   </div>
   <p id="contagem">{{ quantidadeDigitada }}/20</p>
 </div>
</template>

<script>
export default {
 name: "Form",
 data() {
   return {
     textoNovoItem: "",
     novoItemImportante: false,
   };
 },
 computed: {
   quantidadeDigitada() {
     return this.textoNovoItem.length;
   },
 },
 methods: {
   salvarNovoItem() {
     if (this.textoNovoItem.length > 0) {
       const novoItem = {
         id: new Date().getTime(),
         texto: this.textoNovoItem,
         importante: this.novoItemImportante,
         feito: false,
       };
       this.$emit("add-item", novoItem);
       this.textoNovoItem = "";
       this.novoItemImportante = false;
     }
   },
 },
};
</script>