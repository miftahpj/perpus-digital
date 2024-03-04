<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <div class="mb-3">
            <select class="form-control form-control-lg form-select rounded-5">
                  <option value="">Filter...</option>
                  <option value="1">NAMA</option>
                  <option value="2">KEANGGOTAAN</option>
                  <option value="3">WAKTU</option>
                  <option value="4">KEPERLUAN</option>
                </select>
              </div>
        </div>
        <div class="my-3 text-muted">menampilkan 1 dari 1</div>
        <table class="table">
          <thead>
            <tr>
              <td>NO</td>
              <td>NAMA</td>
              <td>KEANGGOTAAN</td>
              <td>WAKTU</td>
              <td>KEPERLUAN</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1.</td>
              <td>Zul Hilmi</td>
              <td>Guru</td>
              <td>24 Februari 2024, 23.31.00</td>
              <td>Baca</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>