<script setup lang="ts">
import Card from "../components/card.vue";
const maisons = [
    {
        nom: "Beverly Springfield",
        prix: "5000",
        favori: true,
        image: "/public/pexels-binyamin-mellish-106399.jpg",
        bath: "2"
    },
    {
        nom: "Beverly Heels",
        prix: "3600",
        favori: false,
        image: "/public/pexels-binyamin-mellish-106399.jpg",
        bath: "3"
    },
]
</script>
<template>
    <div v-for="maison in maisons" :key="maison" class="p-2">
        <h2>page liste</h2>
        <Card v-bind="maison" />
    </div>
</template>