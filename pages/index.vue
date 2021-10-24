<template>
<div>
  <v-container>
    <Publicidad-hys />
  </v-container>

<v-container grid-list-lg>
  <Noticias/>
</v-container>


</div>
</template>


<script>
import Noticias from '@/pages/noticias/index.vue'
export default {
  components:{
    Noticias
  }
}
</script>

