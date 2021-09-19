<template>
  <v-app>
    <v-app-bar
      app
      fixed
    >
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn
        v-for="(item, index) in items"
        :key="index"
        :to="item.to"
        text
        tile
        :ripple="false"
        class="nav-button"
      >
      {{ item.title }}
        <v-icon
          right
          dark
        >
          {{ item.icon }}
        </v-icon>
      </v-btn>
      <v-btn icon @click="toggleDarkMode">
        <v-icon>mdi-brightness-4</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      darkMode: false,
      items: [
        {
          icon: 'mdi-human-greeting',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-account',
          title: 'About Us',
          to: '/about'
        },
        {
          icon: 'mdi-cellphone-basic',
          title: 'Contact',
          to: '/contact'
        }
      ],
      title: 'JK Building'
    }
  },
  methods: {
    toggleDarkMode() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
      this.darkMode = !this.darkMode;
    }
  }

}
</script>

<style lang=scss scoped>
.nav-button {
  background-color: transparent;
  margin: 0 10px;
}

.nav-button::before {
  background-color: transparent;
}

.v-btn--active {
  background-color: none;
  border-bottom: 2px solid $col-primary;
  color: $col-primary;
}
</style>
