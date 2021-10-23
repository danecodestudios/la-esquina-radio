<template>
<v-carousel :height="height" cycle :interval="intervalo" :show-arrows="true" hide-delimiters  >
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
      class="w-100"
      reverse-transition="fade-transition"
      transition="fade-transition"
    >
    
    </v-carousel-item>
  </v-carousel>
</template>

<style scoped>



</style>


<script>
  export default {
    data () {
      return {
        intervalo: 6000,
        items: [
          {
            src: '/hys/01.png',
          },
          {
            src: '/hys/02.png',
          },
          {
            src: '/hys/03.png',
          },
          {
            src: '/hys/04.png',
          },
            {
            src: '/hys/05.png',
          },
        ],
      }
    },

    computed:{
        height () {
        switch (this.$vuetify.breakpoint.name) {
          case 'xs': return 50
          case 'sm': return 80
          case 'md': return 100
          case 'lg': return 135
          case 'xl': return 200
        }
    }
  }
  }
</script>