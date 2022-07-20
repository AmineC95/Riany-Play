<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
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

        </q-toolbar-title>

        <div>
          <img
            alt="Rainy Play logo"
            src="~assets/logo.svg"
            style="width: 150px; height: auto"
          ></div>
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
          Menu
        </q-item-label>

        <EssentialLink
          v-for="link in Menu"
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
    title: 'Accueil',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Recherche',
    icon: 'research',
    link: '/Research'
  },
  {
    title: 'Bibliothèque',
    icon: 'fa-library',
    link: '/Library'
  },


  {
    title: 'Créer une playlist',
    icon: 'plus',
    link: '/Playlist'
  },
  {
    title: 'Titre aimé',
    icon: 'favorite',
    link: '/Likes'
  },

]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      Menu: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
