<script setup>

import { useRoute } from '#imports'
import { Bell } from '@iconoir/vue'

const route = useRoute()
const rotasBloqueadas = ['/freelancer/criar', '/freelancer/perfil', '/usuario/perfil', '/usuario/pagamento']
const rotasLiberadas = ['/freelancer/perfil', '/usuario/perfil', '/usuario/pagamento', '/usuario/login']
</script>

<template>
  <header class="bg-[var(--color-fundo-input)] border-b-2 border-gray-200">
    <div class="flex-grow h-16 flex items-center justify-between px-10 w-full">
      <NuxtLink to="/">
        <img src="../assets/img/Logo.png" alt="Logo" class="h-10" />
      </NuxtLink>

      <NuxtLink
        v-if="!rotasBloqueadas.includes(route.path)"
        to="/freelancer/criar"
      >
        Torne-se um Freelancer
      </NuxtLink>

      <div
        v-if="rotasLiberadas.includes(route.path) && route.path !== '/freelancer/criar' && route.path !== '/usuario/cadastro'"
        class="flex items-center"
      >
        <NuxtLink to="/explorar" class="mr-4">Explorar</NuxtLink>
        <NuxtLink to="/dashboard" class="mr-4">Dashboard</NuxtLink>
        <button class="border-transparent rounded text-black h-auto p-2 cursor-pointer mr-4">
          Mensagens
        </button>
        <button class="border-transparent rounded text-black p-2 cursor-pointer">
          <Bell />
        </button>
        <img src="../assets/img/Lykos-Simbolo.png" alt="Avatar" class="h-10 w-10 rounded-full ml-4" />
      </div>
    </div>
  </header>
</template>
