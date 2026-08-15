<script setup lang="ts">
import { ref } from 'vue'
interface JobApplication {
  jobid: string,
  company: string,
  role: string,
  location: string,
  salary: string,
  status: string
}
const applications=ref<JobApplication[]>([])

const jobid=ref<string>("");
const company=ref<string>("");
const role=ref<string>("");
const location=ref<string>("");
const salary=ref<string>("");
const status=ref<string>("");

const submitForm=()=>{
  const newApplication:JobApplication={
  jobid: jobid.value,
  company: company.value,
  role: role.value,
  location: location.value,
  salary: salary.value,
  status: status.value
  }
  applications.value.push(newApplication)
  jobid.value = ""
  company.value = ""
  role.value = ""
  location.value = ""
  salary.value = ""
  status.value = ""
}
</script>

<template>
  <div class="app">
    <h1>JobTrack</h1>
    <p>Your personal job application manager</p>
    <p>Jobs applied:</p>
    <table border="1">
    <tr>
    <th>Job Id no.</th>
    <th>Company</th>
    <th>Role</th>
    <th>Location</th>
    <th>Salary</th>
    <th>Status</th>
    </tr>
    <tr v-for="application in applications" :key="application.jobid">
    <td>{{application.jobid}}</td>
    <td>{{application.company}}</td>
    <td>{{application.role}}</td>
    <td>{{application.location}}</td>
    <td>{{application.salary}}</td>
    <td>{{application.status}}</td>
    </tr>
    </table>
    <form @submit.prevent="submitForm">
  <p>
    JobId:
    <input v-model="jobid" placeholder="Enter jobid..">
  </p>
  <p>
    Company:
    <input v-model="company" placeholder="Enter company name..">
  </p>

  <p>
    Role:
    <input v-model="role" placeholder="Enter role applied for..">
  </p>

  <p>
    Location:
    <input v-model="location" placeholder="Enter company location..">
  </p>

  <p>
    Salary:
    <input v-model="salary" placeholder="Enter salary offered..">
  </p>

  <p>
    Status:
    <input v-model="status" placeholder="Enter status..">
  </p>

  <button type="submit">Submit</button>
</form>
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
table {
  border-collapse: collapse;
}
th, td {
  padding: 10px;
}
tr:hover {
  transition-duration:1s;
  background-color:#5caee0;
  }
</style>