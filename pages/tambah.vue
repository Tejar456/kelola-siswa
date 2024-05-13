<template>
  <div class="container-fluid p-5">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">ISI BUKU KUNJUNGAN</h2>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <input v-model="form.nis" type="text" placeholder="Nis" class="form-control radius" />
          </div>

          <div class="mb-3">
            <input  v-model="form.nama" type="text" placeholder="Nama" class="form-control radius" />
          </div>

          <div class="mb-3">
            <select  v-model="form.kelas"
              class="form-control form-control-lg form-select radius mb-2"
            >
              <option value="">Kelas</option>
              <option value="X">X</option>
              <option value="XI">XI</option>
              <option value="XII">XII</option>
            </select>
          </div>
          <div class="mb-3">
            <select  v-model="form.jurusan"
              class="form-control form-control-lg form-select radius mb-2"
            >
              <option value="">Jurusan</option>
              <option value="PPLG">PPLG</option>
              <option value="TJKT">TJKT</option>
              <option value="DKV">DKV</option>
              <option value="TSM">TSM</option>
              <option value="TOI">TOI</option>
            </select>
          </div>
          <div class="mb-3">
            <select  v-model="form.nokelas"
              class="form-control form-control-lg form-select radius mb-2"
            >
              <option value="">No Kelas</option>
              <option value="1">1</option>
              <option value="2">2</option>
              <option value="3">3</option>
              <option value="4">4</option>
            </select>
          </div>

          <div class="mb-3">
            <select  v-model="form.jenkelamin"
              class="form-control form-control-lg form-select radius mb-2"
            >
              <option value="">Jenis Kelamin</option>
              <option value="Laki laki">Laki Laki</option>
              <option value="Perempuan">Perempuan</option>
            </select>
          </div>

          <div class="mb-3">
            <input  v-model="form.email"
              type="text"
              placeholder="email"
              class="form-control radius"
            />
          </div>

          <div class="mb-3">
            <input
            v-model="form.nohp"
              type="number"
              placeholder="No Hp"
              class="form-control radius"
            />
          </div>

          <div class="mb-3">
            <input
            v-model="form.alamat"
              type="text"
              placeholder="Alamat"
              class="form-control radius"
            />
          </div>

      

          <div class="tombol">
            <button type="submit" class="btn btn-lg radius" formaction="">
              KIRIM
            </button>
            <nuxt-link to="/">
              <button type="submit" class="btn btn-lg radius kembali">
                KEMBALI
              </button>
            </nuxt-link>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const form = ref({
nis: "",
nama:"",
jenkelamin:"",
alamat:"",
email:"",
nohp:"",
kelas:"",
nokelas:"",
jurusan:"",
})

const kirimData = async() => {
  console.log(form.value)
  const { data, error } = await supabase.from("siswa").insert([form.value])
  if (!error) navigateTo("/data") 
} 
</script>

<style scoped>
.radius {
  border-radius: 25px;
}

input {
  border: 1px solid #000;
  height: 42px;
}

select {
  border: 1px solid #000;
}

button {
  border: 1px solid #000;
  background-color: #265cb5;
  color: #fff;
}

button:hover {
  border: 1px solid #000;
  background-color: #fff;
  color: #265cb5;
}

.kembali {
  position: fixed;
  bottom: 30px;
  right: 30px;
  border-radius: 20px;
}
</style>
