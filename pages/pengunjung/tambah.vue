<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">isi buku kunjungan</h2>
        <from>
          <div class="mb-3">
            <input type="text"class="form-control form-control-lg rounded-5" placeholder="NAMA">
          </div>
          <div class="mb-3">
            <select class="form-control form-control-lg rounded-5">
              <option value="">KEANGGOTAN</option>
              <option value="siswa">siswa</option>
              <option value="guru">guru</option>
              <option value="staf">staf</option>
              <option value="umum">umum</option>
            </select>
          </div>
          <div class="mb-3">
            <div class="row">
              <div class="col-md-4">
              <select class="form-control-lg  from-select rounded-5 mb-2">
                <option value="">TINGKATAN</option>
                <option value="X">X</option>
                <option value="XI">XI</option>
                <option value="XII">XII</option>
              </select>
              </div>
              <div class="col-md-4">
              <select class="from-control form-control-lg rounded-5 mb-2">
                <option value="">JURUSAN</option>
                <option value="PPLG">PPLG</option>
                <option value="DKV">DKV</option>
                <option value="TBSM">TBSM</option>
                <option value="TJKT">TKJT</option>
                <option value="TOI">TOI</option>
              </select>
              </div>
              <div class="col-md-4">
                <select class="from-control form-control-lg form-select rounded-5 mb-2" >
                  <option value="">KELAS</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                </select>
              </div>
              <div class="mb-3">
                <select class="from-control form-control-lg form-select rounded-5 " >
                  <option value="">KEPERLUAN</option>
                  <option value="baca">bacabuku</option>
                  <option value="pinjam">pinjam buku</option>
                  <option value="kebalikan ">kembalikan</option>
                </select>
              </div>
              <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">KIRIM</button>
            </div>
          </div>
        </from>
      </div>
    </div>
  </div>
</template>