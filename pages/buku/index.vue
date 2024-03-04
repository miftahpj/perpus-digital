<template>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
  <div class="container-fluid">
    <div class="row">
    <h2 class="text-center my-4">BUKU</h2>
      <div class="col-lg-12">
        <div class="my-3">
          <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
          <i class="bi bi-search"></i>
        </div>
        <div class="my-3 text-muted">menampilkan 1 dari 1</div>
        <div class="row">
          <div class="col-lg-2">
            <div class="card mb-3">
              <nuxt-link to="/buku/jjk">
                <div class="card-body">
                  <img src="/asset/img/cover1.jpg" class="cover" alt="cover 1">
                </div>
              </nuxt-link>
            </div>
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-body {
  width : 100%;
  height: 250%;
  padding: 0;
}
.cover {
  width : 100%;
  height: 100%;
  objetc-fit: cover;
  objetc-position: 0 30;
}
</style>