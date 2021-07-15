<template>
  <div id="app">
    <h1>Preencha as informações abaixo</h1>

      <CreateUser/>
      <hr>
      <ReadUser/>
  </div>
</template>

<script>
import {eventBus} from './main'
import CreateUser from './components/CreateUser.vue'
import ReadUser from './components/ReadUser.vue'


export default {
  components: {
    CreateUser,
    ReadUser
  },
  data(){
    return {
      dados: {
        type: Object
      }
    }
  },
  created(){
    eventBus.$on('salvar', (dados) => {
      this.dados = dados
    })
  }
}
</script>

<style scoped>
  #app {
    width: 960px;
    margin: 0 auto;
    border: 1px solid blue;
  }
</style>