<template>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>MENU</title>
    </head>
    <body>
      <link
        rel="stylesheet"
        href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
      />
      <div class="container-fluid">
        <div class="row">
          <h2 class="text-center my-4">BUKU</h2>
          <div class="col-lg-12">
            <div class="my-3">
              <form @submit.prevent="getBooks">
                <input
                  v-model="keyword"
                  type="search"
                  class="form-control rounded-5"
                  placeholder="Mau baca apa?"
                />
              </form>
            </div>
            <div>menampilkan {{ books.length }} buku</div>
            <div class="row">
              <div v-for="(book, i) in books" key="i" class="col-lg-2">
                <div class="card mb-3">
                  <NuxtLink :to="`/buku/${book.id}`">
                    <img :src="book.cover" class="cover" alt="cover" />
                  </NuxtLink>
                </div>
              </div>
            </div>
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
    </body>
  </html>
</template>

<style scoped>

.card-body img {
  width: 200px;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
}

.cover {
  height: 350px;
  width: 250px;
  object-fit: cover;
  object-position: 0 30;
  border: none;
  margin-left: 1%;
}

.card {
  border: none;

}
  button {
    border: 1px solid #000;
    background-color: #265cb5;
    color: #fff;
    position: fixed;
    bottom: 30px;
    right: 30px;
    border-radius: 20px;
  }

</style>

<script setup>
const supabase = useSupabaseClient();
const jumlah = ref(0);
const books = ref([]);
const keyword = ref([]);

const getBooks = async () => {
  const { data, error } = await supabase
    .from("buku")
    .select(`*, kategori(*)`)
    .ilike(`judul`, `%${keyword.value}%`);
  if (data) books.value = data;
};

const ambillbuku = async () => {
  const { data, count } = await supabase
    .from("buku")
    .select("*", { count: "exact" });
  if (data) jumlah.value = count;
};

onMounted(() => {
  getBooks();
  // ambilbuku();
});
</script>
