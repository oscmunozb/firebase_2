<template>
    <div>

      <h2 class="mb-3">Registro</h2>
      <form @submit.prevent="register">
      <input class="rounded-2 me-3" type="email" v-model="email" placeholder="Correo Electronico" required>
      <input class="rounded-2 me-3"  type="password" v-model="password" placeholder="Contraseña" required>
      <button class="btn btn-warning" type="submit">Registrarse</button>
    </form>
    </div>
  </template>
   
  <script>
  import { auth, createUserWithEmailAndPassword } from '../auth.js'
   
    export default {
        name: 'CrearUsuario',
      data() {
        return{
          email: '',
          password: ''
        }
      },
      methods:{
        async register(){
          try{
            const userCredential = await createUserWithEmailAndPassword(auth, this.email, this.password)
   
            console.log("Usuario creado",userCredential)
   
            this.email = ''
            this.password = ''

            // Redirigir a la página de inicio (Home) después de crear el usuario
            this.$router.push({ name: 'home' })

          }catch(error){
            console.error(error)
          }
   
        }
      }
    }
  </script>
   
  <style scoped>
  </style>
   