<script setup lang="ts">
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
const maisons = []; // à remplacer par l'appel à Supabase
</script>
<template>
    <h2>page liste - supabase</h2>
    <Card v-for="maison in maisons" :key="maison.nom" v-bind="maison" />
</template>