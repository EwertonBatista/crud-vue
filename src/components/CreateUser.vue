<template>
    <div>
        <form action="" @submit.prevent="salvar">
            <label for="nome">Nome:</label>
            <input 
            required 
            type="text" 
            name="nome"
            v-model="newUser.nome">

            <label for="idade">Idade:</label>
            <input 
            required 
            type="text" 
            name="idade"
            v-model.number="newUser.idade">

            <label for="email"></label>
            <input
            required 
            type="email" 
            name="email"
            v-model="newUser.email">

            <button type="submit">salvar</button>
        </form>
        
    </div>
</template>

<script>

    // Imports
import {eventBus} from './../main'

export default {

    // Data
    data(){
        return {
            newUser: {
                nome: '',
                idade: 18,
                email: ''
            },
            finalUser: {},
            finalUsers: []
        }
    },
    // Methods
    methods: {
        salvar(){
            this.finalUser = Object.assign({}, this.newUser)
            this.finalUsers.push(this.finalUser)
            eventBus.$emit('cadastrar', this.finalUsers)
        }
    }
}
</script>

<style>

</style>