<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">isi buku kunjungan</h2>
        <form @sumbit.prevent="kirimData">
          <div class="mb-3">
            <input v-model="form.nama" placeholder="NAMA" class="form-control form-control-lg form-select rounded-5 mb-2 abu">
          </div>
          <div class="mb-3">
            <select v-model="form.KEANGGOTAAN" class="form-control form-control-lg form-select rounded-5 mb-2 abu">
              <option value="">KEANGGOTAN</option>
              <option v-for="(member, i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
              
            </select>
          </div>
          <div  v-if="form.KEANGGOTAAN == 1" class="mb-3">
            <select v-model="form.JURUSAN" class="form-control form-control-lg form-select rounded-5 mb-2 abu">
                  <option value="">JURUSAN</option>
                  <option value="X PPLG 1">X PPLG 1</option>
                  <option value="X PPLG 2">X PPLG 2</option>
                  <option value="X PPLG 3">X PPLG 3</option>
                  <option value="X PPLG 4">X PPLG 4</option>
                  <option value="XI PPLG 1">XI PPLG 1</option>
                  <option value="XI PPLG 2">XI PPLG 2</option>
                  <option value="XI PPLG 3">XI PPLG 3</option>
                  <option value="XI PPLG 4">XI PPLG 4</option>
                  <option value="XII PPLG 1">XII PPLG 1</option>
                  <option value="XII PPLG 2">XII PPLG 2</option>
                  <option value="XII PPLG 3">XII PPLG 3</option>
                  <option value="XII PPLG 4">XII PPLG 4</option>
                  <option value="X TBSM 1">X TBSM 1</option>
                  <option value="X TBSM 2">X TBSM 2</option>
                  <option value="X TBSM 3">X TBSM 3</option>
                  <option value="X TBSM 4">X TBSM 4</option>
                  <option value="XI TBSM 1">XI TBSM 1</option>
                  <option value="XI TBSM 2">XI TBSM 2</option>
                  <option value="XI TBSM 3">XI TBSM 3</option>
                  <option value="XI TBSM 4">XI TBSM 4</option>
                  <option value="XII TBSM 1">XII TBSM 1</option>
                  <option value="XII TBSM 2">XII TBSM 2</option>
                  <option value="XII TBSM 3">XII TBSM 3</option>
                  <option value="XII TBSM 4">XII TBSM 4</option>
                  <option value="X TJKT 1">X TJKT 1</option>
                  <option value="X TJKT 2">X TJKT 2</option>
                  <option value="X TJKT 3">X TJKT 3</option>
                  <option value="X TJKT 4">X TJKT 4</option>
                  <option value="XI TJKT 1">XI TJKT 1</option>
                  <option value="XI TJKT 2">XI TJKT 2</option>
                  <option value="XI TJKT 3">XI TJKT 3</option>
                  <option value="XI TJKT 4">XI TJKT 4</option>
                  <option value="XII TJKT 1">XII TJKT 1</option>
                  <option value="XII TJKT 2">XII TJKT 2</option>
                  <option value="XII TJKT 3">XII TJKT 3</option>
                  <option value="XII TJKT 4">XII TJKT 4</option>
                  <option value="X DKV 1">X DKV 1</option>
                  <option value="X DKV 2">X DKV 2</option>
                  <option value="XI DKV 1">XI DKV 1</option>
                  <option value="XI DKV 2">XI DKV 2</option>
                  <option value="XII DKV 1">XII DKV 1</option>
                  <option value="XII DKV 2">XII DKV 2</option>
                  <option value="X TOI 1">X TOI 1</option>
                  <option value="XI TOI 1">XI TOI 1</option>
                  <option value="XII TOI 1">XII TOI 1</option>
                  
                </select>
          </div>
          <div class="mb-3">
            <div class="row">
              <div class="mb-3 rounded-5">
                <select v-model="form.KEPERLUAN" class="form-control form-control-lg form-select rounded-5 mb-2 abu">
                  <option value="">keperluan</option>
                  <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
                </select>
              </div>
              <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">KIRIM</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script setup>
const supabase = useSupabaseClient()
const members = ref([])
const objectives = ref([])
const form = ref({
  NAMA: "",
  KEANGGOTAAN: "",
  TINGKATAN: "",
  JURUSAN: "",
  KELAS: "",
  KEPERLUAN: "",
})
const kirimData = async () => {
  console.log(form.value)
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if (!error) navigateTo('/pengunjung')
  else throw error
}
const getKEANGGOTAAN = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if (data) members.value = data
}
const getKEPERLUAN = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if (data) objectives.value = data
}
onMounted(() => {
  getKEANGGOTAAN()
  getKEPERLUAN()
})

</script>