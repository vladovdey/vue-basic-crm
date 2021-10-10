<template>
    <div class="form-container">
        <form action="" method="POST" @submit.prevent="checkUser(login, password)">
            <input type="text" class="basic-input" name="login" v-model="login">
            <input type="password" class="basic-input" name="password" v-model="password">
            <button type="submit">Войти</button>
        </form>
    </div>
</template>

<script>
import router from "../router/index.js"

export default {
    name: "Login",
    data: ()=>{
        return {
            login: "",
            password: ""
        }
    },
    methods:{
        checkUser: async (login, password)=>{
            let response = await fetch('http://localhost:3000/admins');
            let admins = await response.json();
            let resultAdmin = admins.filter(admin => admin.login === login && admin.password === password);
            if(resultAdmin){
                router.push('/info');
            }
        }
    }
}
</script>