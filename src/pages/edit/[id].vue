<script setup lang="ts">
import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
import { supabase } from "@/supabase";
defineProps({
    id: string,
});

</script>
<template>
    <FormulaireOffreMaison :id="id" />
</template>