<template>
    <div>
        Ini Footer
    </div>
    <button @click="increment">increment +</button>
    <button @click="decrement">decrement -</button>
    <button @click="reset">reset </button>
    ||
    <button @click="incrementWithAction">increment with action +</button>
    <button @click="decrementWithAction">decrement with action -</button>
    <button @click="incrementByWithAction(10)">increment By 10 with action </button>
    <hr>
    <button @click="fetchPokemon('ditto')">search pokemon</button>
    <button @click="resetDataPokemon">clear pokemon</button>


</template>

<script setup>
import { useCounterStore } from '../stores/counter';
import { usePokemonStore } from '../stores/pokemon';

const counter = useCounterStore()
const pokemon = usePokemonStore()

const increment = () => {
    counter.$patch((state) => {
        state.count++
    })
}
const decrement = () => {
    counter.$patch((state) => {
        state.count--
    })
}
const reset = () => {
    counter.$reset()
}

// with action
const incrementWithAction = () => {
    counter.increment()
}
const decrementWithAction = () => {
    counter.decrement()
}
const incrementByWithAction = (amount) => {
    counter.incrementBy(amount)
}
const fetchPokemon = (name) => {
    pokemon.getpokemonDetails(name)
}
const resetDataPokemon = () => {
    pokemon.$reset()
}

</script>