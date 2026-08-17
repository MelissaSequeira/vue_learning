<script setup lang="ts">

interface JobApplication {
  jobid: string
  company: string
  role: string
  location: string
  salary: string
  status: string
}

defineProps<{
  applications: JobApplication[]
}>()

const emit = defineEmits<{
  delete: [jobid: string]
}>()

</script>

<template>

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

    <tr
      v-for="application in applications"
      :key="application.jobid"
    >

      <td>{{ application.jobid }}</td>

      <td>{{ application.company }}</td>

      <td>{{ application.role }}</td>

      <td>{{ application.location }}</td>

      <td>{{ application.salary }}</td>

      <td>{{ application.status }}</td>

      <td>
        <button
          @click="emit('delete', application.jobid)"
        >
          Delete
        </button>
      </td>

    </tr>

  </table>

</template>

<style scoped>

table {
  border-collapse: collapse;
  margin-top: 20px;
}

th,
td {
  padding: 10px;
}

tr:hover {
  background-color: #5caee0;
}

</style>