<template>
  <div id="app">
    <h1>Meds Data</h1>
    <div v-for="item in medsData" :key="item.uniqueKey">
      <p>{{ item.batchNo }} | {{ item.temperature }}°C | {{ item.humidity }}%</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      medsData: [],
    };
  },
  mounted() {
    fetch('/api/getAllMedsData') // Adjust the URL to your actual endpoint
        .then(response => response.json())
        .then(data => {
          this.medsData = data;
        })
        .catch(error => console.error('There was an error fetching the data!', error));
  },
};
</script>

<style>
/* Add any styles you need here */
</style>
