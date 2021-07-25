<template>
  <div class="container">
    <article>
      <h1>{{cluster.cluster_name}}</h1>
      <p>{{cluster.cluster_description}}</p>
    </article>
  </div>
</template>

<script>
export default {
  name: 'Clusters',
  layout: 'home',
  data () {
    return {
      id: this.$route.params.id,
    }
  },
  computed: {
    cluster(){
      return this.$store.state.clusters.all.find(cluster => cluster.cluster_id == this.id)
    }
  },
  methods: {
  }
};
</script>
