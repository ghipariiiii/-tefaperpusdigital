<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">BUKU</h2>
        <div class="my-3">
          <form @submit.prevent="getbooks">
          
          </form>
          <input type="search" class="form-control rounded-5" placeholder="mau baca apa hari">
        </div>
        <div class="my-3 text-munted">menampilkan 3 dari 3</div>
        <div class="row">
          <div class="col-lgg-2">
            <div v-for=" (books,i) in books" :key="i" class="col-lg-2">
            <div class="card mb-3">
            <div class="card-body">
              <img  src="" class="cover" alt="buku.judul1">
            </div>
            </div>
            </div>
          </div>
          <div class="col-lg-2">
            <div class="card mb-3">
              <div class="card-body">
                <img src="/assets/img/pulang.jpg" class="buku" alt="buku2">
              </div>
            </div>
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
const supabase = useSupabaseClient()
const books = ref([])

const keyword = ref('')

const getbooks = async () => {
  const { data, error } = await supabase.from('buku').select('*,kategori(*)')
  ilike('judul','%{keyword.value}%')
  if (data) books.value = data

  onMounted(() => {
    getbooks()
  })
}

</script>



<style scoped>
.card-body {
  text-decoration: none;
  width: 100%;
  height: 20em;
  padding: 0;
}

.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>