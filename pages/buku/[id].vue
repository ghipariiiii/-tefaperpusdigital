<template>
  <h2 class="text-start my-4">{{ buku.judul }}</h2>
  <div class="row">
    <div class="col-md-3">
      <div class="card">
        <div class="card-body">
      <span v-if="buku.cover"><img class="cover"  :src="buku.cover"  :alt="buku.judul"></span>
      <span v-else><img src="https://www.google.com/url?sa=i&url=https%3A%2F%2Fralfvanveen.com%2Fen%2Fglossary%2Fplaceholder%2F&psig=AOvVaw3mJm82utBYelgvskF0E28i&ust=1714790433211000&source=images&cd=vfe&opi=89978449&ved=0CBAQjRxqFwoTCIj60tS68IUDFQAAAAAdAAAAABAE" alt="buku.judul1"></span>
        </div>
    </div>
    </div>
    <div class="col-md-6">
      <div class="badge bg-primary p-2">{{ buku.kategori }}</div>
    
      <ul class="list-group list-group-flush">
        <li class="list-group-item">judul: {{ buku.judul }}</li>
        <li class="list-group-item">penulis: {{ buku.penulis }}</li>
        <li class="list-group-item">deskripsi: {{ buku.deskripsi }}</li>
        <li class="list-group-item">tahun_terbit: {{ buku.tahun_terbit }}</li>
        <li class="list-group-item">deskripsi: {{ buku.deskripsi }}</li>
      </ul>
    
    </div>
  </div>
</template>



<script setup>
import { onMounted } from 'vue';
import { useRoute } from 'vue-router';

const supabase = useSupabaseClient()

const route = useRoute()

const buku = ref([])

const getbooksById = async () => {
  const { data,error} = await supabase.from('buku').select(`*, kategori(*)`)
  .eq('id',route.params.id)
  if(data) buku.value = data[0]
}

onMounted(() =>{
  getbooksById()
})
</script>
<style scoped>
.cover{
    width: 100%;
}
</style>