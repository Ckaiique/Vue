<script setup>
import { ref, reactive, onMounted } from 'vue';


const user = reactive({
    email: '',
    password: ''
});

const names = reactive([]);

onMounted(() => {

    names.push(
        {
            firstName: 'Alexandre',
            age: 40
        },
        {
            firstName: 'Joao',
            age: 78
        },
        {
            firstName: 'Maria',
            age: 15
        },
    );

});
function login() {
    console.log(user.email, user.password);
}
function remove(user) {
    const index = names.findIndex(name => name.firstName === user.firstName);
    names.splice(index, 1);
}
</script>

<template>

<h1 class="text-3xl font-bold underline text-red-700">
    Hello world!
  </h1>

    <template v-if="names.length > 0">
        <ul>
            <li v-for="name in names"> {{ name.firstName }} - <button v-on:click="remove">Remove</button></li>
        </ul>
    </template>

    <template v-else>Nenhum user encontrado</template>

    <template v-if="user.email.length <= 0"> Email vazio</template>
    <template v-else="user.email.length <= 0 "> Email {{ user.email }}</template>

    <form action="" @submit.prevent="login">
        <input type="text" placeholder="Email" v-model="user.email">
        <input type="text" placeholder="Password" v-model="user.password">
        <button type="submit">Login</button>
    </form>
</template>

<style></style>