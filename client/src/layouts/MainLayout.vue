<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-white text-primary">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          terzi
        </q-toolbar-title>

        
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Calcular',
    caption: 'Calcular la talla de procesos',
    icon: 'calculate',
    link: '/calculartalla'
  },{
    title: 'Historial',
    caption: 'Historico de cálculos',
    icon: 'timeline',
    link: '/calculartalla'
  },{
    title: 'Informes',
    caption: 'Reportes y Estadisticas',
    icon: 'analytics',
    link: '/calculartalla'
  },
  {
    title: 'Configuraciones',
    caption: 'Configuración de parámetros',
    icon: 'settings',
    link: 'https://github.com/quasarframework'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
