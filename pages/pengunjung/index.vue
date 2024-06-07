<template>
  <div class="wrapper">
    <div class="content"></div>
    <div class="container-fluid text-black" style="padding-top: 160px;">
      <div class="row">
        <div class="col-lg-12 ">
          <h2 class="text-center  ">RIWAYAT KUNJUNGAN</h2>
          <form @submit.prevent="getTotal">
            <input  v-model="keyword"  class="form-control rounded-5 "   placeholder="filter....">
            
            </form>
          
       
          <div class="my-3">menampilkan {{ visitors.length }} dari {{ amountVisitors}}</div>
          <div class="table table-responsive">
            <table class="table table-bordered border-dark text-black ">
              <thead>
                  <tr class="text-center">
                    <td>ID</td>
                    <td>NAMA</td>
                    <td>KATEGORI</td>
                    <td>KELAS</td>
                    <td>KEPERLUAN</td>
                    <td>TANGGAL</td>
                    <td>WAKTU</td>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(visitor,i) in visitors" :key="i" class="text-center">
                    <td>{{ i+1 }}.</td>
                    <td>{{ visitor.nama }}</td>
                    <td>{{ visitor.keanggotaan.nama }}</td>
                    <td>{{ visitor.tingkat}}-{{ visitor.jurusan }}{{ visitor.kelas }}</td>
                    <td>{{ visitor.keperluan.nama }}</td>
                    <td>{{ visitor.tanggal }}</td>
                    <td>{{ visitor.waktu.split(".")[0] }} </td>
                  </tr>
                </tbody>
            </table>
          </div>
          </div>
          <div class="row d-flex justify-content- text-center">
            
            <nuxt-link to="/" class="col-lg-3 col-4 btn btn-dark btn-lg rounded-5 px-5 ">Kembali</nuxt-link>
          </div>
        
          <!-- <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Kembali</button> -->
          </div>
        </div>
      </div>
  </template>
  
  <script setup>
  const supabase= useSupabaseClient()
  const keyword = ref('')
  const visitors = ref([])
  const amountVisitors = ref(0)
  
  const getPengunjung = async () => {
    const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
    if(data) visitors.value = data
  }
  
  async function getAmountVisitors()
  {
      const {data , count} = await supabase.from('pengunjung')
      .select('*', { count: "exact"})
      if (data) amountVisitors.value = count
  }
  const getTotal = async () => {
    const {data,error} = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
        .ilike('nama', `%${keyword.value}%`)
    if(data) visitors.value = data
}
  
  onMounted(() => {
      getPengunjung()
      getAmountVisitors()
      getTotal()
  })
  </script>
  
  <style scoped>
  
  .content {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-size: cover;
    width: 100%;
    height: 100%;
    bottom: 0;
    top: 0;
    left: 0;
    right: 0;
    position: fixed;
    z-index: -1;
  }
  .btn{
    font-family: sans Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    background-color: rgb(255, 255, 255);
    color: rgb(0, 0, 0);
    float :right;
  }
  
  thead, tbody, td{
    border: 2px solid black;
  }
  
  </style> 