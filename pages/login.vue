<template>
  <div>
    <div class="row">
     

      <div class="login col-lg-12">
        <div class="card">
          <h1>Login Form</h1>
          <form @submit.prevent="Login">
            <div class="mb-3">
              <input
                v-model="email"
                type="email"
                class="form-control"
                placeholder="Email"
                aria-describedby="emailHelp"
              />
            </div>
            <div class="mb-3">
              <input
                v-model="password"
                type="password"
                class="form-control"
                placeholder="Password"
              />
            </div>
            <button type="submit" class="btn btn-primary">Login</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const email = ref("");
const password = ref("");

const Login = async () => {
  const { data } = await supabase.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  });

  if (data) {
    navigateTo("/");
  }
};

</script>

<style scoped>
.row {
  height: 80vh;
}

.side {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #0066c5;
}

.logo img {
  width: 70%;
}

.login {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f5f5f5;
}

.login form {
  width: 80%;
}

form input,
button {
  border-radius: 15px;
}

.card {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #ffffff;
  width: 80%;
  height: 50%;
  border-radius: 32px;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
</style>