<template>
  <div class="relative mt-10 flex h-96 w-96 flex-col items-start justify-start">
    <div class="h-48 flex-shrink-0 flex-grow-0 self-stretch">
      <img class="h-56 w-full rounded-lg object-cover" :src="image" />
    </div>
    <div class="
        relative
        flex flex-shrink-0 flex-grow-0 flex-col
        items-start
        justify-start
        gap-4
        self-stretch
        rounded-bl-lg rounded-br-lg
        border-2 border-indigo-50
        bg-white
        px-5
        py-7
      ">
      <div class="relative flex flex-shrink-0 flex-grow-0 items-start justify-start gap-7 self-stretch">
        <div class="relative flex flex-grow flex-col items-start justify-start gap-1.5">
          <div class="relative flex flex-shrink-0 flex-grow-0 items-end justify-start self-stretch">
            <p class="flex-shrink-0 text-left text-2xl font-bold text-indigo-500">${{ prix }}</p>
            <p class="h-8 w-12 flex-shrink-0 flex-grow-0 text-left text-xs text-gray-900 opacity-50">/month</p>
          </div>
          <p class="w-56 flex-shrink-0 flex-grow-0 self-stretch text-left text-2xl font-bold text-gray-900">
            {{ nomMaison }}
          </p>
        </div>
        <heart :class="{ 'fill-red-300': favori }"></heart>
      </div>
      <p class="w-72 flex-shrink-0 flex-grow-0 self-stretch text-left text-base text-gray-900 opacity-50">
        {{ adresse }}
      </p>
      <svg width="306" height="2" viewBox="0 0 306 2" fill="none" xmlns="http://www.w3.org/2000/svg"
        class="flex-shrink-0 flex-grow-0 self-stretch" preserveAspectRatio="xMidYMid meet">
        <line y1="1.25" x2="306" y2="1.25" stroke="#EEF2FF" stroke-width="1.5"></line>
      </svg>
      <div class="flex flex-shrink-0 flex-grow-0 items-start justify-start gap-4 self-stretch">
        <div class="relative flex flex-grow items-center justify-start gap-2">
          <bed></bed>
          <p class="flex-shrink-0 flex-grow-0 text-left text-xs text-gray-500"> {{ nbrChambres }} Beds</p>
        </div>
        <div class="relative flex flex-grow items-center justify-center gap-2">
          <bath></bath>
          <p class="flex-shrink-0 flex-grow-0 text-left text-xs text-gray-500">{{ nbrSDB }} Bathrooms</p>
        </div>
        <div class="relative flex flex-grow items-center justify-end gap-2">
          <meters></meters>
          <p class="flex-shrink-0 flex-grow-0 text-left text-xs text-gray-500">{{ surface }} m??</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import bath from "./icons/bath.vue";
import bed from "./icons/bed.vue";
import meters from "./icons/meters.vue";
import heart from "./icons/heart.vue";


defineProps({
  id_Maison: {type: String},
  nomMaison: { type: String, default: '...' },
  adresse: { type: String, default: '...' },
  prix: { type: Number, default: '...' },
  favori: { type: Boolean, default: false },
  image: { type: String, default: '../../public/pexels-binyamin-mellish-106399.jpg' },
  nbrSDB: { type: Number, default: '...' },
  nbrChambres: { type: Number, default: '...' },
  surface: { type: Number, default: '...' },
})

</script>