<template>
  <v-app>
    <v-navigation-drawer
      color="lightGrey"
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      width="180"
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      color="lightGrey"
      flat
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main class="main-style" >
      <v-container class="mt-0 pt-0">
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      color="lightGrey"
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  name: 'Default',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Create',
          to: '/create'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'heirloomd'
    }
  }
}
</script>

<style scoped>
.main-style {
  width: 100%;
  height: 100%;
  background-color: #f3f4f6
}
</style>
