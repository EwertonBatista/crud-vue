<template>
  <form>
  <div class="form-group" @submit.prevent="enviar">
    <label for="exampleInputEmail1">Login:</label>
    <input 
    type="email" 
    class="form-control" 
    id="exampleInputEmail1" 
    aria-describedby="emailHelp" 
    placeholder="Seu login"
    maxlength="20"
    v-model="cliente.nome">
  </div>

  <div class="form-group">
    <label for="exampleInputPassword1">Senha</label>
    <input 
    type="password" 
    class="form-control" 
    id="exampleInputPassword1" 
    placeholder="Senha"
    maxlength="20"
    v-model="cliente.senha">
  </div>

  <div class="form-group form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Clique em mim</label>
  </div>

  <button 
  type="submit" 
  class="btn btn-primary"
  @click="enviar">Enviar</button>
</form>
</template>

<script>

import { eventBus } from './../main'

export default {
    data(){
        return {
            cliente: {
                nome: '',
                senha: ''
            },
            clientes: [{login: 'ABC', senha: '123'},{login: 'DEF', senha: '456'}]

        }
    },
    methods: {
        enviar(){
            let clienteTemp = {}
            clienteTemp = Object.assign({}, this.cliente)
            this.clientes.push(clienteTemp)
            eventBus.$emit('enviar', clienteTemp)
        }
    }
}
</script>

<style>

</style>