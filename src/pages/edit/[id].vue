<script setup lang="ts">
import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
defineProps({
    id: string,
});

</script>
<template>
    <FormulaireOffreMaison :id="id" />
</template>