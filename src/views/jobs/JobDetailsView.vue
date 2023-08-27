<template>
  <div v-if="job">
    <h1> {{ job.title }} </h1>
    <p>The job Id is {{ job.id }}</p>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <h2>Loading Job details...</h2>
  </div>

</template>

<script>
export default {
    props: ['id'],
    data() {
      return {
        job: null,
      }
    },
    mounted() {
      fetch('http://localhost:3000/jobs/' + this.id)
        .then(res => res.json())
        .then(data => this.job = data)
    }

    // data() {
    //     return {
    //         id: this.$route.params.id,
    //     }
    // }
}
</script>

<style>

</style>