<template>
  <div>
    <h1>Meds Data</h1>
    <table>
      <thead>
      <tr>
        <th>Batch No</th>
        <th>Warehouse No</th>
        <th>Temperature</th>
        <th>Humidity</th>
        <th>Timestamp</th>
        <!-- Add other headers here -->
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in medsData" :key="item.uniqueKey">
        <td>{{ item.batchNo }}</td>
        <td>{{ item.warehouseNo }}</td>
        <td>{{ item.temperature }}</td>
        <td>{{ item.humidity }}</td>
        <td>{{ item.timestamp }}</td>
        <!-- Add other data columns here -->
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
      medsData: [],
    };
  },
  mounted() {
    axios.get('http://149.102.154.14:3000/api/getAllMedsData')
        .then(response => {
          this.medsData = response.data;
        })
        .catch(error => {
          console.error('There was an error!', error);
        });
  },
};
</script>

<style>
/* Add some basic styling to the table */
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  padding: 10px;
  border: 1px solid #ccc;
}
</style>
