<template>
  <div>
    <c-heading text-align="center" mb="4">
      ⚡️ Home page
    </c-heading>
    <c-box bg="primary">
      <h3>Cluster list</h3>
      <ul>
        <li v-for="(related, index) in relatedClusters" :key="index">
          <nuxt-link
            :to="{ name: 'clusters-id', params: { id: related.cluster_id } }"
            >{{ related.cluster_name }}</nuxt-link
          >
        </li>
      </ul>
    </c-box>
    <c-box bg="tomato" mt="30px">
      <h3>Post list</h3>
      <h1 v-if="loading">Loading...</h1>
      <nuxt-link
        v-for="(post, index) in posts"
        :key="index"
        :to="{ name: 'posts-id', params: { id: post.id } }"
      >
        <c-button p="2" mx="5" my="3" bg="primary">
          {{ post.title }}
        </c-button>
      </nuxt-link>
    </c-box>
  </div>
</template>

<script lang="js">
import {
  CHeading,
  CButton,
  CBox,
} from '@chakra-ui/vue'
import axios from 'axios'

export default {
  name: 'App',
  layout: 'home',
  data () {
    return {
      id: this.$route.params.id,
      posts: [],
      loading: false,
    }
  },
  computed: {
    relatedClusters(){
      return this.$store.state.clusters.all.filter(cluster => cluster.cluster_id !== this.id)
    }
  },
  methods: {
  },
  mounted(){
    // const config = {
    //   headers: { Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdXRob3JpemVkIjp0cnVlLCJ0b2tlbl9leHAiOjE2MjY0NTI4MDMsInVzZXJfYXZhdGFyIjoidXNlci9hdmF0YXIvZGVmYXVsdC5qcGciLCJ1c2VyX2VtYWlsIjoieHRlc3Q3QGVtYWlsLmNvbSIsInVzZXJfZnVsbG5hbW1lIjoiRnVsbCBOYW1lIiwidXNlcl9pZCI6MTE0OCwidXNlcl9uYW1lIjoieHRlc3Q3In0._CKyynND70N_mIP2frPXqcX1PUBRotwTRuawLvdewQE` }
    // };
    this.loading = true
    axios.get("https://jsonplaceholder.typicode.com/posts")
    .then(res => {
      this.posts = res.data
      this.loading = false
    })
    .catch(err => {
      console.log("err", err)
      this.loading = false
    })
  }
}
</script>
