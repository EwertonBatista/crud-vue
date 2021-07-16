<template>
    
    <div>
    <div class="jumbotron">
        <h1 class="display-4 owntitle">Crud Vue</h1>
        <p class="lead ownstyle">formulário de cadastro</p>
        <hr class="my-4">
    </div>
        <Main/>
    </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
    components: {
        Main
    }
}
</script>

<style scoped>
    .ownstyle{
        margin-left: 50px;
    }
    .owntitle {
        font-size: 30px;
    }
    
</style>