<script setup lang="ts">
    import Card from "../components/card.vue" ;
    const unObjet = {
        nom: "Beverly Springfield",
        prix: "5000",
        favori: true,
        image: "/public/pexels-binyamin-mellish-106399.jpg",
        bath: "2"

    }
</script>
<template>
    <div class="p-2">
        <h2>page simple</h2>
        <Card v-bind="{nom: 'Beverly Springfield' , prix: 5000 , favori: true , image: '/public/pexels-binyamin-mellish-106399.jpg' , bath: 2 }"></Card>
        <Card v-bind="unObjet"/>
    </div>
</template>

