<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <h1 class="green">Dashboard</h1>
      <p>Übersicht aller Vorgänge</p>
    </div>
  </header>
  <PatientIssueTable :headers="headers" :data="data">
    <template #column0="{ entity }">
      {{ entity.name }}
    </template>
    <template #column1="{ entity }">
      {{ entity.age }}
    </template>
  </PatientIssueTable>
</template>

<script lang="ts">
import PatientIssueTable from '@/components/PatientIssues.vue'

export default {
  components: {
    PatientIssueTable
  },

  data: () => ({
    headers: ['Name', 'Age', 'Favourite Hobbies'],
    data: [
      {
        name: 'James',
        age: 21,
        hobbies: ['tennis', 'coding']
      },
      {
        name: 'Carol',
        age: 22,
        hobbies: ['gaming', 'reading', 'debating']
      },
      {
        name: 'Sam',
        age: 25,
        hobbies: ['brunching', 'going to the gym', 'painting']
      }
    ]
  })
}
</script>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
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
    flex-direction: column;
  }
}
</style>
