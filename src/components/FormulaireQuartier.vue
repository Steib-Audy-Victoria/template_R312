<script setup lang="ts">
defineProps<{
    id?: string;
}>();
//TODO
</script>
<template>
    <FormKit @submit="upsertQuartier" type="form" v-model="quartierCommune" submit-label="Changer"
        :config="{ classes: { input: 'p-1 rounded border-gray-600 shadow-sm border', label: 'text-blue-500', }}"
        :submit-attrs="{ classes: { input: 'bg-blue-500 p-1 rounded text-white' } }">
        <FormKit name="libelle_Quartier" label="libelle du quartier" />
        <FormKit name="libelle_Commune" label="libelle de la commune" />
    </FormKit>
</template>