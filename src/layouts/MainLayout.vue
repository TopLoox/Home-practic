<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="nav-bar">
      <li>
        <a href="#" v-for="icon in icons" :key="icon">
          <q-icon
            size="md"
            color="light-green-5"
            :name="icon"
          />
        </a>
      </li>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  data() {
    return {
      icons: ['home', 'person', 'settings']
    }
  }
})
</script>
