<template>
    <h1 class="mb-6 text-3xl font-extrabold">Home</h1>
    <p class="mb-4">Name in store is:{{ name}}</p>
    <input v-model='newName' 
    type='text' 
    class='border p-2 rounded'/>
    <button 
    @click='saveName' 
    class='border text-white bg-indigo-600'>Submit</button>
</template>

<script setup>
import {useStore} from 'vuex'

import {computed,ref} from 'vue'

const store = useStore()

const name = computed(()=>{
        return store.state.user.name
    })

const newName =ref('')
function saveName(){
    store.dispatch('saveName', newName.value)
    newName.value =''
}


</script>