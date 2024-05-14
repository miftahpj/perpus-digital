<template>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MENU</title>
</head>
<body>
<h2 class="text-start my-4">{{ buku.judul }}</h2>
  <div class="row">
    <div class="col-md-3">
      <img :src="buku.cover" class="cover" alt="cover buku">
    </div>
    <div class="col-md-6">
      <div class="badge bg-primary p-2">{{ buku.kategori }}</div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item">Penulis: {{ buku.penulis }}</li>
          <li class="list-group-item">Penerbit: {{ buku.penerbit }}</li>
          <li class="list-group-item">{{ buku.deskripsi }}</li>
        </ul>
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
</body>
</html>
</template>
<script setup>
const supabase = useSupabaseClient()

const route = useRoute()
const buku = ref ([])

const getBooksByid = async () => {
  const {data, error } = await supabase.from('buku').select(`*, kategori(*)`)
  .eq(`id`, route.params.id)
  if(data) buku.value = data[0]
}
onMounted(() => {
  getBooksByid()
})
</script setup>

<style scoped>
.cover {
  width: 255px;
  height: 370px;
  box-shadow: 1px 10px 50px rgb(0, 0, 0, .5);
}

.card {
  border: none !important;
}

.card-body {
  width: auto;
}
</style>
