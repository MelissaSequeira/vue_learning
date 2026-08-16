<script setup lang="ts">
import { ref ,computed} from 'vue'
interface JobApplication {
  jobid: string,
  company: string,
  role: string,
  location: string,
  salary: string,
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
const deleteApplication=(jobid:string)=>{
applications.value=applications.value.filter(
  application=>application.jobid!==jobid
)
}

const totalApplication=computed(()=>{
  return applications.value.length;
})
const appliedApplication=computed(()=>{
  return applications.value.filter(
    application=>application.status==="Applied"
  ).length;
})
const acceptedApplication=computed(()=>{
  return applications.value.filter(
    application=>application.status==="Accepted"
  ).length;
})
const rejectedApplication=computed(()=>{
  return applications.value.filter(
    application=>application.status==="Rejected"
  ).length;
})


</script>

<template>
  <div class="app">
    <h1>JobTrack</h1>
    <p>Your personal job application manager</p>
    <p>Jobs applied:</p>
    <div>
      <p>Total Jobs Applied : {{totalApplication}}</p>
      <p>Jobs Applied : {{appliedApplication}}</p>
      <p>Accepted : {{acceptedApplication}}</p>
      <p>Rejected: {{rejectedApplication}}</p>
    </div>
    <table border="1">
    <tr>
    <th>Job Id no.</th>
    <th>Company</th>
    <th>Role</th>
    <th>Location</th>
    <th>Salary</th>
    <th>Status</th>
    <th>Action</th>
    </tr>
    <tr v-for="application in applications" :key="application.jobid">
    <td>{{application.jobid}}</td>
    <td>{{application.company}}</td>
    <td>{{application.role}}</td>
    <td>{{application.location}}</td>
    <td>{{application.salary}}</td>
    <td>{{application.status}}</td>
    <td>
      <button @click="deleteApplication(application.jobid)">delete</button>
    </td>
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