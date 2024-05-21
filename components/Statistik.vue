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
    data: [6, 8, 10, 5, 4, 8],
    backgroundColor:[
      'rgb(217,217,217)',
      'rgb(217,217,217)',
      'rgb(217,217,217)',
      'rgb(217,217,217)',
      'rgb(217,217,217)',
      'rgb(217,217,217)'

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