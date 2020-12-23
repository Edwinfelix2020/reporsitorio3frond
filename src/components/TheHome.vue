<template>
<div class="mt-5">

    <div >
        <button type="button" class="btn btn-primary" @click="logOut">Logout</button>
                 
    </div>

    <div class="container mt-4">
        <p>Nombre: {{user.name}}</p>

        <p>Correo: {{user.email}}</p>

    </div>    

</div>
   

</template>

<script>

export default {
    data(){
        return{
            user:{}

        }
    },
     methods:{
        getUserDetails(){
            let user = localStorage.getItem('user');
            let token = localStorage.getItem('jwt');

            if(token){
                this.user = JSON.parse(user);
            }

        },
        logOut(){
            localStorage.removeItem('jwt');
            localStorage.removeItem('user');
            this.$router.push('/');

        }

    },
    created(){
        this.getUserDetails();

    }

    
}
</script>