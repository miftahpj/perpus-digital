<template>
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
  />
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2>pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>

  <h1>statistik</h1>

  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung">
          <div class="card bg-pengunjung2 rounded-5">
            <div class="card-body">
              <p>jumlah pengunjung</p>
              {{ jumlahpengunjung }}
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <div class="card bg-buku2 rounded-5">
          <div class="card-body">
            <h2>Buku</h2>
            {{ jumlahbuku }}
          </div>
        </div>
      </div>
    </div>
  </div>
  <div>
    <ChartComponents />
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const jumlahpengunjung = ref(0);
const jumlahbuku = ref(0);

async function ambiljumlahpengunjung() {
  const { data, error, count } = await supabase
    .from("pengunjung")
    .select("*", { count: "exact" });
  if (count) jumlahpengunjung.value = count;
}

async function ambiljumlahbuku() {
  const { data, error, count } = await supabase
    .from("buku")
    .select("*", { count: "exact" });
  if (count) jumlahbuku.value = count;
}

onMounted(() => {
  ambiljumlahpengunjung();
  ambiljumlahbuku();
});
</script>

<style scoped>
.card {
  height: 300px;
  width: 900px;
  box-shadow: 1px 1px 10px #424242;
}

h2 {
  color: white;
}
.card.bg-pengunjung {
  margin-top: 1%;

  background-image: url("../asset/img/bg2.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}
.card.bg-buku {
  margin-top: 1%;

  background-image: url("../asset/img/bg2.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}
.card.bg-pengunjung2 {
  height: 250px;
  width: 400px;
  box-shadow: 1px 1px 10px #424242;
  margin-top: 1%;
  margin-left: 40%;
  background-color: yellow;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover center;
}
.card.bg-buku2 {
  height: 250px;
  width: 400px;
  box-shadow: 1px 1px 10px #424242;
  margin-top: 1%;
  margin-left: 10%;
  background-color: green;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover center;
}
</style>
