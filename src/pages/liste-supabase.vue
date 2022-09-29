<script setup lang="ts">
import   Card   from "../components/card.vue";
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: Maison, error } = await supabase
    .from('Maison')
    .select('*')
const maisons = Maison;


console.log("Maison", Maison)

</script>
<template>
    <h2 class="m-2">page liste - supabase</h2>
    <div class="m-2">
        <Card v-for="maison in maisons" :key="maison.nomMaison" v-bind="maison" />
    </div>

</template>