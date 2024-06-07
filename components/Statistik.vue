<template>
  <div>
    <canvas id="statistik" width="15px" height="10px"></canvas>
  </div>
</template>
<script setup>
import Chart from 'chart.js/auto'
const labels = [

'january',
'february',
'march',
'april',
'mei',
'june',
];

const data ={
  labels:labels,
  datasets:[{
    label: 'pengunjung',
    data: [6, 8, 10, 6, 7, 10],
    backgroundColor:[
      'rgb(71,190,41)',
      'rgb(238,77,96)',
      'rgb(251,135,28)',
      'rgb(71,190,41)',
      'rgb(238,77,96)',
      'rgb(251,135,28)'

    ],
  }]
};

const config={
  type: 'bar',
  data: data,
  options:{ 
    //maintainAspectRatio:false
    aspectRatio: 3
  }
};

onMounted(() =>{
  const myChart = new Chart(
    document.getElementById('statistik'),
    config
  );
})
</script>