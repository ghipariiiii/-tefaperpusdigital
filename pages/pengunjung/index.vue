<template>
    <div class="cointainer-fluid">
      <div class="row">
         <div class="col-lg-12">
          <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
          <div class="my-3"></div>
          <input type="search" class="form-control-lg rounded-5" placeholder="Filter">
         </div>
         <div class="my-3 text-munted">menampilkan 1 dari 1</div>
         <table class="table">
          <thead>
          <tr>
            <td>#</td>
            <td>NAMA</td>
            <td>KEANGGOTAN</td>
            <td>WAKTU</td>
            <td>KEPERLUAN</td>
          </tr>
          </thead>
          <tbody>
            <tr v-for=" (visitor, i) in visitors" :key="i">
              <td>{{i+1}}</td>
              <td>{{ visitor.NAMA }}</td>
              <td>{{ visitor.KEANGGOTAAN.NAMA }}</td>
              <td>{{ visitor.tanggal }},{{ visitor.waktu }}</td>
              <td>{{ visitor.KEPERLUAN.NAMA }}</td>
            </tr>
          </tbody>
         </table>
      </div>
    </div>
</template>
<script setup>
const supabase = useSupabaseClient()

const visitors = ref([])
const getpengunjung = async() =>{
  const{data,error} =await supabase.form('pengunjung').select('*,KEANGGOTAAN(*),KEPERLUAN(*)')
  if ( data )visitors.value=data
  onMounted(()=> {
    getpengunjung()

  })
}
</script>