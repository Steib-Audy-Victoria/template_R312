<script setup lang="ts">
import { supabase } from "@/supabase"
import { ref } from 'vue'
import Card from "./card.vue";
import { useRouter } from "vue-router";
const router = useRouter();
const maison = ref({});

const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la maison
    let { data, error } = await supabase
        .from("Maison")
        .select("*")
        .eq("id", props.id);
    if (error) console.log("n'a pas pu charger le table Maison :", error);
    else maison.value = (data as any[])[0];
}

async function upsertMaison(dataForm, node) {
    const { data, error } = await supabase.from("Maison").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
        node.setErrors([]);
        router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}
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
            <FormKit @submit="upsertMaison" type="form" v-model="maison" submit-label="Changer"
                :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
                :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
                <FormKit name="nomMaison" label="Nom" />
                <FormKit name="adresse" label="Adresse" />
                <FormKit name="prix" label="Prix" type="number" />
                <FormKit name="nbrSDB" label="Nombre de salle de bain" type="number" />
                <FormKit name="nbrChambres" label="Nombres de chambres" type="number" />
            </FormKit>
        </div>
    </div>
</template>