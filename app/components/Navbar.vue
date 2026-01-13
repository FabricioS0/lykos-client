<script setup lang="ts">
import { useRoute } from 'vue-router'
import { Bell } from '@iconoir/vue'
import { computed } from 'vue'
const route = useRoute()

const inicio = ['usuario-inicio', 'usuario-inicio-logado']
const produtos = ['usuario-produto', 'freelancer-produto']
const bloqueadasFreelancer = [
  'freelancer-criar',
  'freelancer-perfil',
  'usuario-perfil',
  'usuario-pagamento'
]
const PacoteServicos = ['freelancer-PacoteServicos']
const botaomensagem = ['usuario-inicio']
const excluirMensagem = ['usuario-inicio-logado']
const dashboardUsuario = ['usuario-perfil']



const mostrarExplorar = computed(() =>
  inicio.includes(String(route.name)) || produtos.includes(String(route.name))
  || bloqueadasFreelancer.includes(String(route.name)) 
)

const mostrarFreelancer = computed(() =>
  !bloqueadasFreelancer.includes(String(route.name)) ||
  inicio.includes(String(route.name)) ||
  produtos.includes(String(route.name)) ||
  dashboardUsuario.includes(String(route.name))
)

const mostrarDashboard = computed(() =>
  !produtos.includes(String(route.name)) &&
  !inicio.includes(String(route.name)) &&
  !dashboardUsuario.includes(String(route.name))
)

const mostrarEntradas = computed(() =>
  !PacoteServicos.includes(String(route.name))  && !excluirMensagem.includes(String(route.name))
  || botaomensagem.includes(String(route.name)) 
  
)

console.log('NAME:', route.name, 'PATH:', route.path)
</script>
<template>
  <header class="bg-[var(--color-fundo-input)] border-b-2 border-gray-200">
    <div class="flex-grow h-16 flex items-center justify-between px-10 w-full">

      <NuxtLink to="/">
        <img src="../assets/img/Logo.png" alt="Logo" class="h-10" />
      </NuxtLink>

      <div v-if="route.name !== 'freelancer-criar'" class="flex items-center">

        <!-- AGORA APARECE -->
        <NuxtLink
          v-if="mostrarExplorar && route.name !=='usuario-cadastro'"
          to="/explorar"
          class="mr-4 text-black"
        >
          Explorar
        </NuxtLink>

        <NuxtLink
          v-if="mostrarFreelancer "
          to="/freelancer/criar"
          class="mr-4 text-black"
        >
          Torne-se um Freelancer
        </NuxtLink>

        <NuxtLink
          v-if="mostrarDashboard && route.name !=='usuario-cadastro' && route.name !=='usuario-login' "
          to="/dashboard"
          class="mr-4 text-black"
        >
          Dashboard
        </NuxtLink>

        <button v-if="route.name !=='usuario-cadastro' && route.name !=='usuario-login' && (produtos || !mostrarEntradas)" class="border-transparent rounded-lg text-black h-auto p-2 cursor-pointer mr-4 bg-gray-200">
          Mensagens
        </button>

        <button v-if="route.name !=='usuario-cadastro' && route.name !=='usuario-login' && (produtos || !mostrarEntradas)"  class="border-transparent rounded-lg bg-gray-200 text-black p-2 cursor-pointer">
          <Bell />
        </button>

        <img v-if="route.name !=='usuario-cadastro' && route.name !=='usuario-login' && (produtos || !mostrarEntradas)" 
          src="../assets/img/Lykos-Simbolo.png"
          alt="Avatar"
          class="h-10 w-10 rounded-full ml-4"
        />

        <button v-if="mostrarEntradas && !produtos"  class="border-transparent rounded-lg text-black h-auto p-2 cursor-pointer mr-4 bg-[var(--color-laranja)] text-white">
          Cadastre-se
        </button>
        <button v-if="mostrarEntradas && !produtos" class="border-transparent rounded-lg text-black h-auto p-2 px-4 cursor-pointer mr-4 bg-gray-200">
          Entrar
        </button>
      </div>
    </div>
  </header>
</template>
