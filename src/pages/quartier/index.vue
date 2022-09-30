<script setup lang="ts">
import { supabase } from "../../supabase";
import groupBy from "lodash/groupBy";
import {
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
} from '@headlessui/vue'


const { data, error } = await supabase.from("quartierCommune").select("*");

if (error) console.log("n'a pas pu charger la view allUsers qui regroupe les code & lib quartier & commune :", error);

</script>

<template>
    <section class="m-2 flex flex-col">
        <h3 class="text-2xl">Liste des quartiers</h3>
        <ul>
            <li v-for="quartierCommune in (data as any[])">
                {{ quartierCommune.libelle_Commune }} -
                {{ quartierCommune.libelle_Quartier }}
            </li>
        </ul>
    </section>
    <hr class="my-4">
    <section class="m-2 flex flex-col">
        <Disclosure v-for="(liste_Quartier, libelle_Commune) in groupBy(
        data,
        'libelle_Commune'
        )" :key="libelle_Commune">
            <DisclosureButton>{{libelle_Commune}}</DisclosureButton>
            <DisclosurePanel>
                <ul>
                    <li v-for="quartier in liste_Quartier" :key="quartier.code_Quartier"> 
                    <RouterLink :to="{ name: 'quartier-id', params: { id: quartier.code_Quartier }, }">{{quartier.libelle_Quartier}}</RouterLink>
                    </li>
                </ul>
            </DisclosurePanel>
        </Disclosure>
    </section>
</template>