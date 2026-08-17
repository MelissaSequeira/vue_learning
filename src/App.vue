<script setup lang="ts">
import { ref, computed } from 'vue'
import JobForm from './components/JobForm.vue'
import JobTable from './components/JobTable.vue'

export interface JobApplication {
  jobid: string
  company: string
  role: string
  location: string
  salary: string
  status: string
}

const applications = ref<JobApplication[]>([
  {
    jobid: "JOB-101",
    company: "JP Morgan Chase",
    role: "Software Engineer I",
    location: "Mumbai",
    salary: "7 LPA",
    status: "Applied"
  },
  {
    jobid: "JOB-102",
    company: "TCS",
    role: "Software Developer",
    location: "Pune",
    salary: "6 LPA",
    status: "Accepted"
  },
  {
    jobid: "JOB-103",
    company: "Infosys",
    role: "Frontend Developer",
    location: "Bengaluru",
    salary: "5.5 LPA",
    status: "Rejected"
  },
  {
    jobid: "JOB-104",
    company: "Accenture",
    role: "Associate Software Engineer",
    location: "Mumbai",
    salary: "6.5 LPA",
    status: "Applied"
  },
  {
    jobid: "JOB-105",
    company: "Deloitte",
    role: "Software Engineer",
    location: "Hyderabad",
    salary: "8 LPA",
    status: "Accepted"
  }
])

const totalApplication = computed(() => {
  return applications.value.length
})

const appliedApplication = computed(() => {
  return applications.value.filter(
    application => application.status === "Applied"
  ).length
})

const acceptedApplication = computed(() => {
  return applications.value.filter(
    application => application.status === "Accepted"
  ).length
})

const rejectedApplication = computed(() => {
  return applications.value.filter(
    application => application.status === "Rejected"
  ).length
})

const submitForm = (newApplication: JobApplication) => {
  applications.value.push(newApplication)
}

const deleteApplication = (jobid: string) => {
  applications.value = applications.value.filter(
    application => application.jobid !== jobid
  )
}
</script>

<template>
  <div class="app">

    <h1>JobTrack</h1>
    <p>Your personal job application manager</p>

    <h3>Application Statistics</h3>

    <div>
      <p>Total Jobs Applied: {{ totalApplication }}</p>
      <p>Jobs Applied: {{ appliedApplication }}</p>
      <p>Accepted: {{ acceptedApplication }}</p>
      <p>Rejected: {{ rejectedApplication }}</p>
    </div>

    <JobTable
      :applications="applications"
      @delete="deleteApplication"
    />

    <JobForm
      @submit-application="submitForm"
    />

  </div>
</template>

<style scoped>
.app {
  padding: 30px;
}

h1 {
  font-size: 32px;
}

p {
  color: gray;
}
</style>