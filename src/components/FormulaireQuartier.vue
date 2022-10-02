<script setup lang="ts">
import { supabase } from "@/supabase"
import { ref } from 'vue'
import { useRouter } from "vue-router";
const router = useRouter();
const quartier = ref({});
const quartierObject = ref({});


const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la table quartier
    let { data, error } = await supabase
        .from("Quartier")
        .select("*")
        .eq("code_Quartier", props.id);
    if (error) console.log("n'a pas pu charger le table Quartier :", error);
    else quartier.value = (data as any[])[0];
}

//Ajout / modification quartier
async function upsertQuartier(dataForm, node) {
    const { data, error } = await supabase.from("Quartier").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
        node.setErrors([]);
        router.push({ name: "quartier-id", params: { id: data[0].code_Quartier } });
    }
}

// Charger les données des communes
const { data: listeCommune, error } = await supabase
    .from("Commune")
    .select("*");
if (error) console.log("n'a pas pu charger la table Commune :", error);
// Les convertir par `map` en un tableau d'objets {value, label} pour FormKit
const optionsCommune = listeCommune?.map((Commune) => ({
    value: Commune.code_Commune,
    label: Commune.libelle_Commune,
}));


//suppression quartier

async function supprimerQuartier() {
    const { data, error } = await supabase
        .from("Quartier")
        .delete()
        .match({ code_Quartier: quartierObject.value.code_Quartier });
    if (error) {
        console.error(
            "Erreur à la suppression de ",
            quartierObject.value,
            "erreur :",
            error
        );
    } else {
        router.push("/quartier");
    }
}

</script>


<template>
    <FormKit @submit="upsertQuartier" type="form" submit-label="Envoyer"
        :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
        :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
        <FormKit name="libelle_Quartier" label="libelle du quartier" />
        <FormKit type="select" name="code_Commune" label="Commune" :options="optionsCommune" />
    </FormKit>
    <hr class="m-2">
    
    <section>
        <button type="button" v-if="quartierObject.code_Quartier" @click="($refs.dialogSupprimer as any).showModal()"
            class="focus-style justify-self-end rounded-md bg-red-500 p-2 shadow-sm">
            Supprimer l'offre
        </button>
        <dialog ref="dialogSupprimer" @click="($event.currentTarget as any).close()">
            <button type="button" class="focus-style justify-self-end rounded-md bg-blue-300 p-2 shadow-sm">
                Annuler</button><button type="button" @click="supprimerQuartier()"
                class="focus-style rounded-md bg-red-500 p-2 shadow-sm">
                Confirmer suppression
            </button>
        </dialog>
    </section>
</template>