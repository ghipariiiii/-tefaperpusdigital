<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah/">
          <div class="card  bg-pengunjung rounded-5">
          <div class="card-body">
            <h2>PENGUJUNG</h2>
          </div>
          </div>
        </nuxt-link>
      </div>
      
      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5 topright T ">
            <div class="card-body">
              <h2>CARI BUKU</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      
  <div class="Container-fluid">
    <div class="row justify-content-evenly rounded-3">
      <div class="col-4">
        <div class="card1">
         
          <div class="raccing">
          <nuxt-link to="/pengunjung">
            <h2 style="font-size: 50px; margin-right: 80px "><span class="no">{{ jml_pengunjung }}</span>Pengunjung</h2>
          </nuxt-link>
          </div>
        </div>
      </div>
      <div class="col-4">
        <statistik/>
      </div>
      <div class="col-4">
        <div class="raccing1">
          <nuxt-link to="/buku">
            <h2 style="font-size: 50px; margin-right: 80px "><span class="no">{{ jml_buku }}</span>buku</h2>
          </nuxt-link>
        </div>
      </div>
    </div>
     
      </div>
      
    </div>
  </div>
</template>
<script setup>
const supabase = useSupabaseClient()
const jml_pengunjung = ref(0)
const jml_buku = ref(0)

async function getjml_pengunjung() {
  const{error, data, count } = await supabase
  .from("pengunjung")
  .select('*', {count: 'exact' })
  if (count) jml_pengunjung.value = count
}

async function getjml_buku() {
  const{error, data, count } = await supabase
  .from("buku")
  .select('*', {count: 'exact' })
  if (count) jml_buku.value = count
}

onMounted(() => {
getjml_pengunjung()
getjml_buku( )
})

</script>


<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px  10px #424242;
}
.card.bg-pengunjung {
  background-image: url("../assets/img/bg-kunjungan.png");
  background-repeat: no-repeat;
  background-position: center center ;
  background-size: cover;
  height: 353px ;
  width: 336px;
}
.card.bg-buku {
  background-image:url("../assets/img/bg-buku3.png") ;
  background-size: cover;
  background-repeat:no-repeat ;
  height: 353px ;
  width: 336px;
}
.topright {
  position: absolute;

  right: 15px;
}
.T {
  width: 100%;
}
.raccing {
  margin-top: 50px;
  width: 400px;
  height: 100px;
  box-shadow: 1px 1px 10px;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color:   #20D4BF;
}
.raccing1 {
  margin-left: auto;
  margin-top:50px ;
  width: 400px;
  height: 100px;
  box-shadow: 1px 1px 10px;
  border-radius: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color:   #20D4BF;
}
</style>