<script setup>
import { computed, ref } from 'vue';

let newItem = ref('');
let i = 1;
let items = ref([
    {id: i++, name:'Sai', isDone: false},
    {id: i++, name:'leib', isDone: true},
    {id: i++, name:'piim', isDone: false},
    {id: i++, name:'juust', isDone: false},
]);

function addItem(){
    if(newItem.value.trim() !== ''){
        items.value.push({id: i++, name:newItem.value.trim(), isDone: false});
    }
    newItem.value = '';
}

let doneItems = computed(() => items.value.filter(item => item.isDone));
let toDoItems = computed(() => items.value.filter(item => !item.isDone));

</script>

<template>
    <div class="container content mt-2">
        <div class="field has-addons">
            <div class="control is-expanded">
                <input @keydown.enter="addItem" v-model= "newItem" class="input" type="text" placeholder="Add Item">
            </div>
            <div class="control">
                <button class="button is-info" @click="addItem()">
                    Add Item
                </button>
            </div>
        </div>

        <h1>All Items</h1>
        <ul>
            <li v-for="item in items":key="item.id">
                {{ item.name }}
                <input type="checkbox" v-model="item.isDone"></input>
            </li>
        </ul>

        <h1>Done Items</h1>
        <ul>
            <li v-for="item in doneItems" :key="item.id">
                {{ item.name }}
                <input type="checkbox" v-model="item.isDone"></input>
            </li>
        </ul>

        <h1>ToDo Items</h1>
        <ul>
            <li v-for="item in toDoItems" :key="item.id">
                {{ item.name }}
                <input type="checkbox" v-model="item.isDone"></input>
            </li>
        </ul>
    </div>
</template>