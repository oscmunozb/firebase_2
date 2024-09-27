<template>
    <div>
        <h2 class="mb-3">Inicio de Sesion</h2>
        <input class="rounded-2 me-3" type="email" v-model="email" placeholder="Correo Electronico">
        <input class="rounded-2 me-3" type="password" v-model="password" placeholder="Contraseña">
        <button class="btn btn-success" @click="signIn">Iniciar Sesión</button>
        <!-- <router-link to="/register">No tienes una cuenta? Registrate</router-link> -->
    </div>
</template>
 
<script>
import { auth , signInWithEmailAndPassword } from '../auth.js'
 
export default {
    data(){
        return{
            email: '',
            password: ''
        }
    },
    methods:{
        async signIn(){
            try {
                await signInWithEmailAndPassword(auth, this.email, this.password)
 
                const redirectPath = this.$route.query.redirect || '/'
 
                this.$router.push(redirectPath)
 
            } catch (error) {
                console.error("Error al iniciar sesion", error.message)
                alert("Error al iniciar sesion: " + error.message)
 
 
            }
        }
    }
 
}
 
</script>