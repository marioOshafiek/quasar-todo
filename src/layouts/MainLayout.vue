<template>
  <q-layout view="hHh lpR fFf">
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

        <q-toolbar-title> One List </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Navigation </q-item-label>
        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer reveal bordered class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar
            text-color="white"
            icon="playlist_add_check"
            font-size="30px"
            size="50px"
          />
        </q-toolbar-title>
        <q-tabs active-color="blue">
          <q-route-tab
            v-for="link in linksList"
            :key="link.title"
            :icon="link.icon"
            :label="link.title"
            :to="link.link"
          />
        </q-tabs>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { defineComponent } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Todo",
    caption: "todo list",
    icon: "list",
    link: "/",
  },
  {
    title: "Settings",
    caption: "Change app settings",
    icon: "settings",
    link: "/settings",
  },
  {
    title: "About",
    caption: "about the app",
    icon: "info",
    link: "/about",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  data() {
    return {
      linksList,
      leftDrawerOpen: false,
    };
  },

  methods: {
    toggleLeftDrawer() {
      this.leftDrawerOpen = !this.leftDrawerOpen;
    },
  },
});
</script>
