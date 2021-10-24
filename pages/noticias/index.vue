<template>
  <v-layout row wrap>
    <v-flex
      justify-content-center
      xs12
      sm6
      md4
      xl3
      v-for="post in posts"
      :key="post.slug"
    >
    <NuxtLink :to="'/noticias/' + post.slug">
      <v-card max-width="344">
        <v-img :src="post.jetpack_featured_media_url" height="200px"></v-img>

        <v-card-title v-html="post.title.rendered"> </v-card-title>

        <v-card-actions>
          <v-btn color="pink accent-3" text> Hace : 5 Minutos </v-btn>

          <v-spacer></v-spacer>
          <h4>{{ categoria }}</h4>
        </v-card-actions>
      </v-card>
        </NuxtLink>
    </v-flex>
  </v-layout>
</template>

<script>
import axios from 'axios'
// import moment from 'moment'
// require('moment/locale/es-mx')
export default {
  data() {
    return {
      posts: [],
      categoria: '',
      show: false,
      // moment: moment,
    }
  },

  async mounted() {
    const res = await axios.get('https://laesquinaradio.co/wp-json/wp/v2/posts')
    this.posts = res.data
    console.log(this.posts)

    // ================= PETICION CATEGORIA  ==================================
    let _id = res.data[0].categories[0]
    const resCategorias = await axios.get(
      `${'https://laesquinaradio.co/wp-json/wp/v2/categories/'}${_id}`
    )
    this.categoria = resCategorias.data.name
  },
}
</script>