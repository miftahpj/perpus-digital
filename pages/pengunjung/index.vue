<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form @submit.prevent="getPengunjung">
            <input
              v-model="keyword"
              type="search"
              class="form-control form-control-lg rounded-5"
              placeholder="Cari Pengunjung"
            />
          </form>
        </div>
        <div class="my-3 text-muted">
          menampilkan {{ visitors.length }} dari {{ jumlah }}
        </div>
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
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
              <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
  <nuxt-link to="../"
    ><button
      type="submit"
      class="btn btn-lg rounded-5 px-5 bg-secondary text-white"
      style="float: right"
    >
      KEMBALI
    </button></nuxt-link
  >
</template>

<script setup>
const supabase = useSupabaseClient();
const jumlah = ref(0);
const visitors = ref([]);
const keyword = ref("");

const getPengunjung = async () => {
  const { data, error } = await supabase
    .from("pengunjung")
    .select(`*, keanggotaan(*), keperluan(*)`)
    .ilike(`nama`, `%${keyword.value}%`)
    .order("id", { ascending: false });
  if (data) visitors.value = data;
};
const totalPengunjung = async () => {
  const { data, count } = await supabase
    .from("pengunjung")
    .select("*", { count: "exact" });
  if (data) jumlah.value = count;
};

onMounted(() => {
  getPengunjung();
  totalPengunjung();
});
</script>
