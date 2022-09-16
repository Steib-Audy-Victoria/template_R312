<script setup lang="ts">
import { ref } from "@vue/reactivity";
import Card from "./card.vue";
// On fait une variable réactive qui réference les données
// ATTENTION : faire une Ref pas une Reactive car :
// c'est l'objet qui doit être réactif, pas ses props
const maison = ref({});
</script>

<template>
    <div>
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
            <!-- Optionnel on affiche les données -->
            <Card v-bind="maison" />
        </div>
        <div class="p-2 mt-5">
            <!--On passe la "ref" à FormKit-->
            <FormKit type="form" v-model="maison" submit-label="Envoyer"
                :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
                :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
                <FormKit name="nom" label="Nom" />
                <FormKit name="prix" label="Prix" type="number" />
                <FormKit name="favori" label="Mettre en valeur" type="checkbox" wrapper-class="flex" />
            </FormKit>
        </div>
    </div>
</template>