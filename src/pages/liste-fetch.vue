<script setup lang="ts">
const res = await fetch("src/assets/maisons.json");
const maisons = await res.json();

import Card from "../components/card.vue";
</script>
<template>
    <h2>page liste</h2>
    <Card v-for="maison in maisons" :key="maison.nom" v-bind="maison" />
</template>