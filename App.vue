<template>
  <div>
    <h1>Group List</h1>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Created By</th>
          <th>Created Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="group in groups" :key="group.id">
          <td>{{ group.id }}</td>
          <td>{{ group.name }}</td>
          <td>{{ group.created_by }}</td>
          <td>{{ group.created_date }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      groups: []
    };
  },
  mounted() {
    this.fetchGroups();
  },
  methods: {
    fetchGroups() {
      const headers = {
        'X-API-Key': 'd5846540'
      };
      axios.get('https://my.api.mockaroo.com/groups', { headers })
        .then(response => {
          this.groups = response.data;
        })
        .catch(error => {
          console.error('There was an error fetching the groups:', error);
        });
    }
  }
};
</script>

<style>
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
}
th {
  background-color: #f4f4f4;
}
</style>
