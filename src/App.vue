<script setup>
import { ref } from 'vue';

    let message = ref('Hello vue');

    
</script>

<template>
    <div class="container content mt-2">
        <button class="button is-primary" @click="message = 'Hello KTA24'">Click me!</button>
        <input class="input" v-model="message"></input>
        <h1>{{ message.split('').reverse().join('') }}</h1>
    </div>
</template>