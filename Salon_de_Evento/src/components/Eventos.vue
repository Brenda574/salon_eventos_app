<script>
import axios from 'axios';

export default {
  data() {
    return {
      usuario: '',
      contraseña: '',
    };
  },
  methods: {
    login(event) {
      event.preventDefault();

      axios.post('http://127.0.0.1:8000/api/login/', {
        usuario: this.usuario,
        contraseña: this.contraseña,
      })
        .then(response => {
          // El inicio de sesión fue exitoso
          const redirect = response.data.redirect;
          const usuario = response.data.usuario;
          const rol = response.data.rol;
          console.log('Redireccionando a:', redirect);
          // Realiza las acciones necesarias, como redireccionar a la página corresspondiente en Vue.js
          window.location.href = redirect;
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

<style>

</style>