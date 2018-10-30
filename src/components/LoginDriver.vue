<template>
    <div class="container background">
      <div class="row">
        <div class="col-12">
          <p id="title" class="text-center" >HERE WE BUS</p>
          <form @submit.prevent="login">
            <div id="container-form" class="form-group">
              <input class="input form-control" type="text" placeholder="Nombre(s)">
              <input class="input form-control" type="text" placeholder="Apellidos">
              <input class="input form-control" type="text" placeholder="ID">
              <input class="input form-control" type="text"  placeholder="Escuela">
              <input class="input form-control" type="password" placeholder="Contraseña">
            </div>
            <div>
              <button id="button" class="btn btn-dark">Crear Cuenta</button>
            </div>
            <div>
              <a id="create" href="#">¿Ya tienes una cuenta?</a>
            </div>
          </form>
        </div>
      </div>

      <!-- <i class="fas fa-question-circle"></i> -->
    </div>
</template>

<script>
import firebase from 'firebase';

export default {
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    login() {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
        .then(user => this.$router.replace('Home'), error => console.error(error));
    },
  },
};
</script>

<style scoped>

  .background {
    background-color: #7dbae4;
    margin-top: 80px;
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    color: #0f1621;
  }

  p {
    text-align: center;
  }

  #title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 36px;
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

   #create {
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
    margin-top: 62px;
    margin-left: 14px;
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

    /* #title {
      margin-left: 127px;
    } */

    #container-form {
      margin-left: 69px;
    }

    #reset {
      margin-left: 494px;
    }
 }

</style>
