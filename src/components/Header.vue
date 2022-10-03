<template>
    <div>
        Ini Header
    </div>
    <pre>from state: {{ counter }}</pre>
    <pre>from getters: {{ getCount }}</pre>
    <pre>from getters doubleCount: {{ doubleCount }}</pre>
    <pre>from getters dividedBy with params: {{ dividedCountBy }}</pre>
    <pre>Action with API Pokemon: {{ pokemon }}</pre>
</template>

<script setup>
    import { computed } from 'vue';
    import { useCounterStore } from '../stores/counter';
    import { usePokemonStore } from '../stores/pokemon'

    const counterStore = useCounterStore()
    const pokemonStore = usePokemonStore()

    const counter = computed(() => counterStore.count)
    // static getters
    const getCount = computed(() => counterStore.getCount)
    const doubleCount = computed(() => counterStore.doubleCount)
    // dynamic getters with params
    const dividedCountBy = computed(() => counterStore.dividedCountBy(2))

    // get state after action
    const pokemon = computed(() => pokemonStore.pokemonDetails)

    counterStore.$subscribe((mutation, state) => {
        console.log(mutation, state)
    })
</script>