<template>
  <div>
      <h1>List</h1>

      <hr>

      <table v-if="tasks.length">
        <thead>
          <tr>
            <th>#</th>
            <th>Title</th>
            <th>Date</th>
            <th>description</th>
            <th>Status</th>
            <th>Open</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(task, idx) of tasks"
            :key="task.id"
          >
            <td>{{ idx + 1 }}</td>
            <td>{{ task.title }}</td>
            <td>{{ new Date(task.date).toLocaleDateString() }}</td>
            <td class="td"><div class="text">{{ task.description }}</div></td>
            <td>{{ task.status }}</td>
            <td>
              <router-link tag="button" class="btn btn-small" :to="'/task/' + task.id">
                Open
              </router-link>
            </td>
          </tr>
        </tbody>
      </table>
      <p v-else>No Tasks</p>
  </div>
</template>

<script>
export default {
  computed: {
    tasks() {
      return this.$store.getters.tasks
    }
  }
}
</script>

<style lang="scss" scoped>
.td {
  max-width: 400px;
}
.text {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
</style>