<script setup lang="ts">
import { ref } from 'vue'

interface JobApplication {
  jobid: string
  company: string
  role: string
  location: string
  salary: string
  status: string
}

const jobid = ref("")
const company = ref("")
const role = ref("")
const location = ref("")
const salary = ref("")
const status = ref("")

const emit = defineEmits<{
  'submit-application': [application: JobApplication]
}>()

const submitForm = () => {

  const newApplication: JobApplication = {
    jobid: jobid.value,
    company: company.value,
    role: role.value,
    location: location.value,
    salary: salary.value,
    status: status.value
  }

  emit('submit-application', newApplication)

  jobid.value = ""
  company.value = ""
  role.value = ""
  location.value = ""
  salary.value = ""
  status.value = ""
}
</script>

<template>

  <form @submit.prevent="submitForm">

    <p>
      Job ID:
      <input
        v-model="jobid"
        placeholder="Enter job ID.."
      >
    </p>

    <p>
      Company:
      <input
        v-model="company"
        placeholder="Enter company name.."
      >
    </p>

    <p>
      Role:
      <input
        v-model="role"
        placeholder="Enter role applied for.."
      >
    </p>

    <p>
      Location:
      <input
        v-model="location"
        placeholder="Enter company location.."
      >
    </p>

    <p>
      Salary:
      <input
        v-model="salary"
        placeholder="Enter salary offered.."
      >
    </p>

    <p>
      Status:
      <input
        v-model="status"
        placeholder="Enter status.."
      >
    </p>

    <button type="submit">
      Submit
    </button>

  </form>

</template>

<style scoped>

form {
  margin-top: 30px;
}

input {
  margin-left: 10px;
}

</style>