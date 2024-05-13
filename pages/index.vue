<template>
  <div class="container-fluid font">
   
    <div class="statistik">
    </div>
    <div class="row my-5 d-flex justify-content-around">
      
      <div class="col-sm-5 mb-3 kartu">
          <NuxtLink to="data">
          <div class="card c2 rounded-5">
            <div class="card-body text">
          
            <h3 class="pt-4">Data Siswa</h3>
          </div>
        </div>
      </NuxtLink>
      </div>
    
    <div class="col-sm-5 kartu">
        <NuxtLink to="tambah">
        <div class="card c2 rounded-5">
          <div class="card-body text">
            
            <h3 class="pt-4">Tambah Data Siswa</h3>
          </div>
        </div>
      </NuxtLink>
      </div>
    </div>

  </div>
</template>



<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #17161633;
}


.card-body > h4 {
  color: #fff;
  position: absolute;
  bottom: 5px;
  right: 15px;
}

.statistik {
  margin-left: 100px;
}

/* .kartu {
  width: 40%;
} */

.c2 {
  border: 1px solid #000;
}

.text {
  display: flex;
  justify-content: center;
  align-items: center;
}

.no {
  font-size: 70px;
}
</style>