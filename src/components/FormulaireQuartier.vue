<script setup lang="ts">
import { supabase } from "@/supabase"
import { ref } from 'vue'
import { useRouter } from "vue-router";
const router = useRouter();
const quartier = ref({});

const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la maison
    let { data, error } = await supabase
        .from("Quartier")
        .select("*")
        .eq("code_Quartier", props.id);
    if (error) console.log("n'a pas pu charger le table Quartier :", error);
    else quartier.value = (data as any[])[0];
}

async function upsertQuartier(dataForm, node) {
    const { data, error } = await supabase.from("Quartier").upsert(dataForm);
    if (error) node.setErrors([error.message])
    else {
        node.setErrors([]);
        router.push({ name: "quartier-id", params: { id: data[0].code_Quartier } });
    }
}



</script>
<template>
    <FormKit @submit="upsertQuartier" type="form" submit-label="Changer"
        :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
        :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
        <FormKit name="libelle_Quartier" label="libelle du quartier" />
        <!--<FormKit name="libelle_Commune" label="libelle de la commune" />-->
    </FormKit>
</template>