<template>
    <div class="container background">
      <div class="row">
        <div class="col-12">
          <p id="title">HERE <br>
             WE <br>
             BUS</p>
          <form @submit.prevent="login">
            <div id="container-form" class="form-group">
              <input class="input form-control" type="email" v-model="email" placeholder="Correo electrónico">
              <input class="input form-control" type="password" v-model="password" placeholder="Contraseña">
              <a id="reset" href="#">Forgot your password</a>
            </div>
            <div>
              <button id="button" class="btn btn-dark">Iniciar Sesión</button>
            </div>
            <div>
              <a id="create" href="#">¿No tienes una cuenta?</a>
            </div>
          </form>
        </div>
      </div>
    </div>
</template>

<script>
import firebase from 'firebase'
export default {
    data () {
    return {
      email: '',
      password: ''
    }
},
methods: {
    login () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
        .then((user) => this.$router.replace('Home'), (error) => console.error(error))
    }
  }
}
</script>

<style scoped>

  .background {
    background-color: #7dbae4;
    margin-top: 80px;
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
  }

  p {
    text-align: left;
    margin-left: 49px;
    justify-content: flex-start;
  }

  #title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 36px;
    align-items: flex-start;
  }

  .input {
    background-color: #ffffff;
    width: 250px;
    margin-left: 50px;
    align-items: flex-end;
  }
  #button {
    justify-content: center;
    margin-top: 22px;
    height: 48px;
  }

  form > * {
    display: block;
  }

  #reset, #create {
    text-decoration: none;
    color: #000000;
  }

  #reset {
    margin-left: 45px;
  }

  .form-group #reset a {
    align-items: flex-end;
    margin-right: 1px;
    font-size: 7px;
  }

  #container-form {
    margin-top: 27px;
  }
  /* Tamaños de pantalla */
@media screen and (min-width:575px) {
  #button {
    width: 213px;
    font-size: 28px;
    height: 68px;
    margin-top: 47px;
  }
  #title {
    font-size: 60px;
    align-items: flex-end;
    margin-top: 26px;
    font-size: 75px;
  }
  #container-form {
    margin-left: 6px;
  }

  .input {
    width: 590px;
    height: 85px;
    font-size: 26px;
  }
  #reset {
    margin-left: 207px;
  }
  #reset, #create {
    font-size: 28px;
  }
}

@media screen and (min-width: 992px) {
    .input {
      width: 890px;
    }

    #title {
      margin-left: 127px;
    }

    #container-form {
      margin-left: 69px;
    }

    #reset {
      margin-left: 494px;
    }
 }

</style>