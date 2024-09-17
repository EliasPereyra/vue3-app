<script setup>
import { ref } from 'vue'

const jobs = ref([
  { id: 1, title: 'farm worker', location: 'lon lon ranch' },
  { id: 2, title: 'quarryman', location: 'death mountain' },
  { id: 3, title: 'flute player', location: 'the lost woods' },
  { id: 4, title: 'chess player', location: 'the royal road' },
  { id: 5, title: 'musician', location: 'mt. hoon hoo' }
])

const title = ref('')
const location = ref('')

const addJob = (e) => {
  if (title.value.trim() !== '') {
    jobs.value.push({ id: 6, title: title.value, location: location.value })
  } else {
    alert('Please enter a job title')
  }
}
const deleteJob = (id) => {
  jobs.value = jobs.value.filter((job) => job.id !== id)
}
</script>

<template>
  <h1>Jobs available</h1>
  <p v-if="jobs.length > 0">THere are jobs available</p>
  <p v-else>There are no jobs available</p>
  <ul>
    <li v-for="job in jobs" :key="job.id">
      <p>{{ job.title }}</p>
      <small>{{ job.location }}</small>
      <button @click="deleteJob(job.id)">Delete job</button>
    </li>
  </ul>

  <section>
    <h3>Add a Job</h3>
    <form @submit.prevent="addJob" class="form">
      <label for="title">Job Title</label>
      <input type="text" name="title" id="title" v-model="title" />

      <label for="location">Job Location</label>
      <input type="text" name="location" id="location" v-model="location" />

      <button type="submit">Add job</button>
    </form>
  </section>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 400px;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
