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
      {{ entity.patientID }}
    </template>
    <template #column1="{ entity }">
      {{ entity.patientName }}
    </template>
    <template #column2="{ entity }">
      {{ entity.studyDate }}
    </template>
    <template #column3="{ entity }">
      {{ entity.bodyPartExamined }}
    </template>
    <template #column4="{ entity }">
      {{ entity.dataIsUploaded ? '✅' : '🚫' }}
    </template>
    <template #column5="{ entity }">
      {{ entity.printingIsSuccessful ? '✅' : '🚫' }}
    </template>
    <template #column6="{ entity }">
      {{ entity.errorMessage ? entity.errorMessage : '' }}
    </template>
  </PatientIssueTable>
</template>

<script lang="ts">
import PatientIssueTable from '@/components/PatientIssues.vue'

const calculatedDate = new Date().toLocaleDateString('de-DE')

export default {
  components: {
    PatientIssueTable
  },

  data: () => ({
    headers: ['ID', 'Name', 'Datum', 'Körperteil', 'Hochgeladen', 'Ausgedruckt', 'Fehlermeldung'],
    data: [
      {
        patientID: 1,
        patientName: 'James',
        studyDate: calculatedDate,
        bodyPartExamined: 'Knee',
        dataIsUploaded: true,
        printingIsSuccessful: true,
        errorMessage: null
      },
      {
        patientID: 2,
        patientName: 'Carol',
        studyDate: calculatedDate,
        bodyPartExamined: 'Abdomen',
        dataIsUploaded: true,
        printingIsSuccessful: true,
        errorMessage: null
      },
      {
        patientID: 3,
        patientName: 'Sam',
        studyDate: calculatedDate,
        bodyPartExamined: 'Foot',
        dataIsUploaded: true,
        printingIsSuccessful: false,
        errorMessage:
          'Fehler beim Drucken der PDF – es konnte keine Verbindung zum Drucker hergestellt werden. Prüfen Sie die Verbindung und versuchen Sie es erneut.'
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
