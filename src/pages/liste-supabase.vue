<script setup lang="ts">
import   Card   from "../components/card.vue";
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: Maison, error } = await supabase
    .from('Maison')
    .select('*')
const maisons = Maison; // à remplacer par l'appel à Supabase


console.log("Maison", Maison)


async function upsertMaison(dataForm, node) {
    const { data, error } = await supabase.from("Maison").upsert(dataForm);
    if (error) node.setErrors([error.message])
}
</script>
<template>
    <h2>page liste - supabase</h2>
    <div><Card v-for="maison in maisons" :key="maison.nomMaison" v-bind="maison" /></div>

    <div  class="p-2 mt-8">   
        <FormKit type="form" submit-label="Envoyer" @submit="upsertMaison" :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
                :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
            <FormKit name="nomMaison" label="Nom" />
            <FormKit name="adresse" label="Adresse" />
            <FormKit name="prix" label="Prix" type="number" />
            <FormKit name="nbrSDB" label="Nombre de salle de bain" type="number" />
            <FormKit name="nbrChambres" label="Nombres de chambres" type="number" />
        </FormKit>
    </div>
</template>