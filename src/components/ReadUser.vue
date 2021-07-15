<template>
  <div>
      <h2>Lista de cadastrados:</h2>
      <ul>
          <li v-for="(cadastrado,indice) in cadastrados"
          :key="indice"> {{cadastrado.nome}} {{cadastrado.idade}} {{cadastrado.email}} </li>
      </ul>
  </div>
</template>

<script>

import {eventBus} from './../main'

export default {
    data(){
        return {
            cadastrados: {
                type: Array
            }
        }
    },
    created(){
        eventBus.$on('cadastrar', (lista) => {
            this.cadastrados = lista
        })
    }

}
</script>

<style>

</style>