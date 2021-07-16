<template>
 
 <tbody>
    <tr class="ownspace">
      <th scope="row">Cliente:</th>
      <td>{{clientes.nome}}</td>
      <td>{{clientes.senha}}</td>
      <button type="button" class="btn btn-warning est ownbutton" @click="editar">Editar</button>
      <button type="button" class="btn btn-danger">Deletar</button>
    </tr>
  </tbody>

</template>

<script>
import {eventBus} from './../main'

export default {
    props: {
        clientes: Object
    },
    data(){
        return {
            
        }
    },
    methods: {
        editar(){
            eventBus.$emit('editar', this.clientes)
        }
    }
}
</script>

<style scoped>
    .ownbutton {
        margin: 0px 15px 0px;
    }
    .ownspace {
        margin: 10px 0px;
    }
</style>

