<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>This job id is {{ id }}</p>
    <h1>{{ job.details }}</h1>
  </div>
  <div v-else>
    <p>Loading job detalils...</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    }
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  }
};
</script>

<style></style>
