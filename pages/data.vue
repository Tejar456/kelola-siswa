<template>
  <div class="contsinaer-fluid">
    <div class="row">
      <div class="col-lg-12 p-5">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <form @submit.prevent="cariPengunjung">
          <div class="my-3">
            <input
              v-model="keyword"
              type="search"
              class="form-control rounded-5"
              placeholder="Mau baca apa hari ini?"
            />
          </div>
        </form>
        <div class="my-3 text-muted">
          Menampilkan {{ datasiswa.length }} dari {{ countsiswa }}
        </div>
        <table class="table table-bordered">
          <thead>
            <tr>
              <td>NO</td>
              <td>NAMA</td>
              <td>NIS</td>
              <td>KELAS</td>
              <td>JENIS KELAMIN</td>
              <td>ALAMAT</td>
              <td>EMAIL</td>
              <td>NO HP</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(siswa, i) in datasiswa" :key="i">
              <td>{{ i + 1 }}.</td>
              <td>{{ siswa.nama }}</td>
              <td>{{ siswa.nis }}</td>
              <td>{{ siswa.kelas }} {{ siswa.jurusan }} {{ siswa.nokelas }}</td>
              <td>{{ siswa.jenkelamin }}</td>
              <td>{{ siswa.alamat }}</td>
              <td>{{ siswa.email }}</td>
              <td>{{ siswa.nohp }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <nuxt-link to="/">
      <button type="submit" class="btn ms-3 btn-lg">KEMBALI</button>
    </nuxt-link>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();


const datasiswa = ref([]);
const countsiswa = ref(0);
const keyword = ref("");

const getData = async () => {
  const { data, error } = await supabase
    .from("siswa")
    .select(`*`)
    .order("id", { ascending: false });
  if (data) datasiswa.value = data;
};

const countVisitor = async () => {
  const { data, count } = await supabase
    .from("siswa")
    .select("*", { count: "exact" });
  if (data) countsiswa.value = count;
};

const cariPengunjung = async () => {
  const { data, error } = await supabase
    .from("siswa")
    .select(`*`)
    .ilike("nama", `%${keyword.value}%`);
  if (data) datasiswa.value = data;
};

onMounted(() => {
  getData();
  countVisitor();
});
</script>

<style scoped>
button {
  border: 1px solid #000;
  background-color: #265cb5;
  color: #fff;
  position: fixed;
  bottom: 30px;
  right: 30px;
  border-radius: 20px;
}

button:hover {
  border: 1px solid #000;
  background-color: #fff;
  color: #265cb5;
}
</style>
