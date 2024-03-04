<script setup lang="ts">
import Chart from 'chart.js/auto';

const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'My First dataset',
      backgroundColor: 'rgb(255, 99, 132)',
      borderColor: 'rgb(255, 99, 132)',
      data: [10, 10, 5, 2, 20, 30, 45],
    }]
  };


  const config = {
    type: 'bar',
    data: data,
    options: {}
  };

onMounted(() => {
    const myChart = new Chart(
    document.getElementById('myChart'),
    config
  );
})
</script>

<template>
    <div>
        <canvas id="myChart"></canvas>
      </div>
      
</template>