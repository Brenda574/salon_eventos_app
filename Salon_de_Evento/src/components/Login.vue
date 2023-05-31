
<template>
    <div class="container py-5 h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-xl-10">
          <div class="card rounded-3 text-black" style="background-color: #b5c1b7;">
            <div class="row g-0">
              <div class="col-lg-6">
                <div class="card-body p-md-5 mx-md-4">
                  <div class="text-center">
                    <img src="https://cdn-icons-png.flaticon.com/512/8915/8915119.png" style="width: 80px;" alt="logo">
                  </div>
                  <div class="text-center">
                    <img src="https://www.aimmedia.com/wp-content/uploads/2022/10/GardenGate_LOGO_FINAL-600x250_554e45.png"
                      style="width: 185px;" alt="logo">
                  </div>
                  <form @submit="login" style="padding-top: 2rem">
                    <div class="form-outline mb-4">
                      <input type="text" v-model="usuario" class="form-control" placeholder="Usuario" />
                    </div>
                    <div class="form-outline mb-4">
                      <input type="password" v-model="password" class="form-control" placeholder="Contraseña" />
                    </div>
                    <div class="text-center pt-1 mb-5 pb-1">
                      <div>
                        <button class="btn boton4 custom-2 mb-3" type="submit" style="background-color: #E1D5D5; transition: all 0.35s;">Iniciar sesión</button>
                      </div>
                    </div>
                  </form>
                </div>
              </div>
              <div class="col-lg-6 d-flex align-items-center gradient-custom-2 ard rounded-3"
                style="background-image: url(https://i.pinimg.com/564x/d6/9c/09/d69c096f70ab897a5318d1788809d967.jpg); background-size : 550px  750px; background-repeat : no-repeat">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        usuario: '',
        password: '',
      };
    },
    methods: {
    login(event) {
      event.preventDefault();

      axios.post('http://127.0.0.1:8000/api/login/', {
        usuario: this.usuario,
        password: this.password,
      })
        .then(response => {
          const eventos = response.data.eventos;
          const usuario = response.data.usuario;
          const rol = response.data.rol;
          console.log('Redireccionando a:', eventos);
          // Realiza las acciones necesarias, como redireccionar a la página corresspondiente en Vue.js
          //window.location.href = redirect;
          //router.push({ name: redirect, params: { id: usuario, rol: rol } });

        })
        .catch(error => {
          // El inicio de sesión falló
          console.error(error.response.data.message);
        });
    },
  },

  };
  </script>