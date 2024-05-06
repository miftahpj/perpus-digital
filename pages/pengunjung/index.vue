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

const visitors = ref([]);

const getPengunjung = async () => {
  const { data, error } = await supabase
    .from("pengunjung")
    .select(`*, keanggotaan(*), keperluan(*)`);
  if (data) visitors.value = data;
};

onMounted(() => {
  getPengunjung();
});
</script>
