<template>
  <nav>
    <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul>
      <li>
        <router-link class="text-red-600 underline" to="/">
          lien vers
          <code class="font-mono">/src/pages/index.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/simple">
          lien vers
          <code class="font-mono">/src/pages/simple.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste">
          lien vers
          <code class="font-mono">/src/pages/liste.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste-fetch">
          lien vers
          <code class="font-mono">/src/pages/liste-fetch.vue</code>
        </router-link>
      </li>
      <hr class="my-2">
      <li>
        <router-link class="text-red-600 underline" to="/liste-supabase">
          lien vers
          <code class="font-mono">/src/pages/liste-supabase.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/new">
          lien vers
          <code class="font-mono">/src/pages/edit/new.vue</code>
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/[id]">
          lien vers
          <code class="font-mono">/src/pages/edit/[id].vue</code>
        </router-link>
      </li>
      <hr class="my-2">
      <li>
        <router-link class="text-red-600 underline" to="/login-logout">
          lien vers
          <code class="font-mono">/src/pages/login-logout.vue</code>
        </router-link>
      </li>
      <hr class="my-2">
      <li>
        <router-link class="text-red-600 underline" to="/quartier">
          lien vers
          <code class="font-mono">/src/pages/quartier/index.vue</code>
        </router-link>
      </li>
            <li>
              <router-link class="text-red-600 underline" to="/quartier/new">
                lien vers
                <code class="font-mono">/src/pages/quartier/new.vue</code>
              </router-link>
            </li>

    </ul>
  </nav>


  <!-- Affiche les pages -->
  <Suspense>
    <router-view class="m-2 border-2 p-2" />
  </Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from '@heroicons/vue/20/solid'
</script>
