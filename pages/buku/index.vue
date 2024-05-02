<template>
  <div class="container-fluid">
  <div class="row">
  <div class="col-lg-12">
  <h2 class="text-center my-4">BUKU</h2>
  <div class="my-3">
  <input type="search" class="from-control rounded-5" placeholder="mau baca apa hari">
</div>
<div class="my-3 text-munted">menampilkan 3 dari 3</div>
<div class="row">
  <div class="col-lgg-2">
    <div class="card mb-3">
      <div class="card-body">
        <img src="~/asset/img/buku hujan.jpg" class="buku" alt="buku1">
      </div>
    </div>
  </div>
  <div class="col-lg-2">
    <div class="card mb-3">
      <div class="card-body">
        <img src="~/asset/img/pulang.jpg" class="buku" alt="buku2">
      </div>
    </div>
  </div>
  <div class="col-lg-2">
    <div class="card mb-3">
      <div class="card-body">
        <img src="~/asset/img/gadis kretek ratih kumala" class="buku" alt="buku3">
      </div>
    </div>
  </div>
</div>
</div>
</div>
</div>
</template>
<style scoped>
.card-body{
  text-decoration: none;
  width: 100%;
  height: 20em;
  padding: 0;
} 
.cover{
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position:0 30 ;
}
</style>