<template>
  <v-app >
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
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

    <v-app-bar :clipped-left="clipped" fixed app class="black">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />

      <v-toolbar class="black text-center">
        <Logo-transp />
        <v-spacer />
         <v-divider
      class="mx-4 pink darken-3"
      vertical

    ></v-divider>
         <h6 class="text-sm-body-2">{{ titleEmisora }}</h6>
        <v-btn class="p-3 ml-4 pink accent-3" icon @click.stop="sonido()">
          <v-icon v-if="!pausa" class="p-4" size="45">mdi-motion-play-outline</v-icon>
          <v-icon v-if="pausa" class="p-4" size="45">mdi-motion-pause-outline</v-icon>
        </v-btn>
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app>
      <span>&copy; LA ESQUINA RADIO {{ new Date().getFullYear() }} </span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {

      // EMISORA 
      audio : null,
      pausa: false,
// ====================

      clipped: true,
      drawer: false,
      fixed: true,
      items: [
        {
          icon: 'mdi-home',
          title: 'INICIO',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'NOTICIAS',
          to: '/noticias',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'LA ESQUINA RADIO ',
      titleEmisora: 'EMISORA EN VIVO',
      to: '/',
    }
  },

     mounted() {
    this.$store.commit('initializeSound');
  },

    methods: {
    sonido() {

   
      if (this.pausa == false || this.isSoundEnabled) {
        this.audio = new Audio("http://stream.zeno.fm/459vbcprnd0uv")
        this.audio.play()
        this.pausa = true
      } else {
        this.audio.pause()
        this.pausa = false
      }
    },
  },
computed: {
    isSoundEnabled() {
      return this.$store.state.isSoundEnabled;
    },
  }
}
</script>


<style>
a{
  text-decoration: none;
}

img{
  width: 100%  !important;
}
</style>
