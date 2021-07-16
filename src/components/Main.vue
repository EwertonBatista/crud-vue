<template>
  <div class="AppPrincipal">
      <!-- ENTRADA DE DADOS -->
      <div class="infos">
          <h1>Preencha as informações abaixo</h1>

          <Form/>
          
      </div>

      <!-- SAIDA DE DADOS -->
<div class="saida">
          <h2>Cadastrados:</h2>
        
        <thead>
  <table class="table">

        <tr>
            <th scope="col">#</th>
            <th scope="col">Login</th>
            <th scope="col">Senha</th>
        </tr>

            <Saida 
            v-for="cliente in clientes"
            :key="cliente.login"
            :clientes="cliente"
            @editar="clienteEditar = $event"/>

  </table>
        </thead>

        
</div>


  </div>
</template>

<script>

import Form from './Form.vue'
import Saida from './Saida.vue'
import {eventBus} from './../main'

export default {
    components: {
        Form,
        Saida
    },
    data(){
        return {
            clientes: [],
            clienteEditar: undefined
        }
    },
    methods: {
        aplicarSelecao(cliente){
            return {
                selecionar: this.clienteEditar && this.clienteEditar.nome === cliente.nome
            }
        }
    },
    created(){
        eventBus.$on('enviar', (clientes) => {
            this.clientes.push(clientes)
        })
        eventBus.$on('editar', (cliente) => {
            this.clienteEditar = cliente
        })
    }
}
</script>

<style>
 .AppPrincipal {
        display: flex;
        justify-content: space-between;
    }

    .infos{
        padding: 50px;
        border-right: 5px solid rgb(0, 0, 0);
        width: 700px;
    }
    .saida {
        padding: 50px;
        width: 700px;
    }

</style>