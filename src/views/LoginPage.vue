<template>
    <div class="loginPage">
    <div class="card card0" style="box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19)">
        <div class="d-flex flex-lg-row flex-column-reverse">
            <div class="card card1">
                <div class="row justify-content-center my-auto">
                    <div class="col-md-8 col-10 my-5">
                        <div class="row justify-content-center px-3 mb-3"> <img id="logo" src="../assets/logo.png"> </div>
                        <h3 class="mb-5 text-center heading"><strong>TADIKA MESRA</strong></h3>
                        <!-- <h6 class="msg-info">Login dulu baru mesen!</h6> -->
                        <form @submit.prevent="login">
                            <div class="form-group">
                                <label class="form-control-label text-muted">Email</label>
                                <input v-model="email" type="text" id="email" name="email" placeholder="Mana coba emailnya" class="form-control">
                            </div>
                            <div class="form-group">
                                <label class="form-control-label text-muted">Password</label>
                                <input v-model="password" type="password" id="psw" name="psw" placeholder="Sini sini password" class="form-control">
                            </div>
                            <div class="row justify-content-center my-3 px-3">
                                <button type="submit" class="btn-block btn-color">Masok</button>
                            </div>
                        </form>
                    </div>
                    <!-- <GoogleLogin class="row justify-content-center" :params="params" :renderParams="renderParams" :onSuccess="onSuccess" :onFailure="onFailure"></GoogleLogin> -->
                </div>
                <div class="bottom text-center mb-5">
                    <p href="#" class="sm-text mx-auto mb-3">Bukan warga sini?<button class="btn btn-white ml-2" @click.prevent="goToRegister">Join dulss</button></p>
                </div>
            </div>
            <div class="card card2">
                <div class="my-auto mx-md-5 px-md-5 right">
                    <h3 class="text-white"><strong>DICARI</strong></h3> <br><small class="text-white" style="display: block; text-align: left !important;">Halo ges, Tadika Mesra lagi kekurangan guru neh. Ya gimana ya namanya juga sekolah boongan. Kamu daripada maen instagram mulu mending daftar.</small>
                    <button class="btn btn-white mt-5" @click.prevent="goToRegister">Daftar</button>
                </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
// import axios from '../config/axiosInstance'
import Swal from 'sweetalert2'

export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    goToRegister () {
      this.$router.push('/register')
    },
    login () {
      const obj = {
        email: this.email,
        password: this.password
      }
      //   axios({
      //     method: 'post',
      //     url: '/login',
      //     data: obj
      //   })
      this.$store.dispatch('login', obj)
        .then(response => {
          localStorage.setItem('access_token', response.data.access_token)
          this.$router.push('/home')
        })
        .catch(error => {
          const message = error.response.data
          console.log(message)
          Swal.fire({
            title: message,
            icon: 'error'
          })
        })
    }
  }
}
</script>

<style>
#app {
    display: flex;
    /* align-items: center; */
    /* display: flex; */
    /* flex-wrap: wrap; */
    min-width: 100%;
    justify-content: center;
    padding: 0;
    margin: 0;
}

@media only screen and (min-width: 950px) {
   .loginPage {
      padding-left: 10%;
      padding-right: 10%;
      position: relative;
      transform: translate(-50%, 5%);
      top: 50%;
      left: 50%;
   }
}
.loginPage {
    @padding-large-vertical:         10px;
    @padding-large-horizontal:       16px;
    /* background-color: red; */
    /* padding: 2vmin; */
    /* position: relative; */
    /* display: flex; */
    /* align-items: center; */
    /* justify-content: center; */
    /* top: 50%; */
    /* left: 50%; */
    /* transform: translate(-50%, 5%); */
    /* padding: 25px 300px 0px 300px; */
    /* margin-bottom: 100px */
}

input,
textarea {
    background-color: #F3E5F5;
    border-radius: 50px !important;
    padding: 12px 15px 12px 15px !important;
    width: 100%;
    box-sizing: border-box;
    border: none !important;
    border: 1px solid #F3E5F5 !important;
    font-size: 16px !important;
    color: #000 !important;
    font-weight: 400
}

input:focus,
textarea:focus {
    -moz-box-shadow: none !important;
    -webkit-box-shadow: none !important;
    box-shadow: none !important;
    border: 1px solid #007991 !important;
    outline-width: 0;
    font-weight: 400
}

button:focus {
    -moz-box-shadow: none !important;
    -webkit-box-shadow: none !important;
    box-shadow: none !important;
    outline-width: 0
}

.card {
    border-radius: 0;
    border: none
}

.card1 {
    width: 50%;
}

.card2 {
    width: 50%;
    background-image: linear-gradient(to right, #007991, #78ffd6)
}

#logo {
    width: 100px;
}

.heading {
    margin-bottom: 60px !important;
    font-size: 25px;
}

::placeholder {
    color: #000 !important;
    opacity: 1
}

:-ms-input-placeholder {
    color: #000 !important
}

::-ms-input-placeholder {
    color: #000 !important
}

.form-control-label {
    font-size: 12px;
    margin-left: 0
}

.msg-info {
    padding-left: 15px;
    margin-bottom: 30px
}

.btn-color {
    border-radius: 50px;
    color: #fff;
    background-image: linear-gradient(to right, #007991, #78ffd6);
    padding: 15px;
    cursor: pointer;
    border: none !important;
    margin-top: 40px
}

.btn-color:hover {
    color: #fff;
    background-image: linear-gradient(to right, #78ffd6, #007991)
}

.btn-white {
    border-radius: 50px;
    color: #007991;
    background-color: #fff;
    padding: 8px 40px;
    cursor: pointer;
    border: 2px solid #007991 !important
}

.btn-white:hover {
    color: #fff;
    background-image: linear-gradient(to right, #78ffd6, #007991)
}

a {
    color: #000
}

a:hover {
    color: #000
}

.bottom {
    width: 100%;
    margin-top: 50px !important
}

.sm-text {
    font-size: 15px
}

@media screen and (max-width: 992px) {
    .card1 {
        width: 100%;
        padding: 40px 30px 10px 30px
    }

    .card2 {
        width: 100%
    }

    .right {
        margin-top: 100px !important;
        margin-bottom: 100px !important
    }
}

@media screen and (max-width: 768px) {
    .container {
        padding: 10px !important
    }

    .card2 {
        padding: 50px
    }

    .right {
        margin-top: 50px !important;
        margin-bottom: 50px !important
    }
}
</style>
