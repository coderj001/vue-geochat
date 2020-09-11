<template>
    <div class="container">
        <div class="row">
            <h3>Register</h3>
            <form class="col s12" @submit.prevent="register">
                <div class="row">
                    <div class="input-field col s12">
                        <i class="material-icons prefix">email</i>
                        <input id="email" type="email" class="validate" v-model="email" />
                        <label for="email">Email</label>
                    </div>
                </div>
                <div class="row">
                    <div class="input-field col s12">
                        <i class="material-icons prefix">lock</i>
                        <input id="password" type="password" class="validate" v-model="password" />
                        <label for="password">Password</label>
                    </div>
                </div>
                <div class="row">
                    <div class="input-field col s12">
                        <i class="material-icons prefix">lock</i>
                        <input id="password2" type="password" class="validate" v-model="repassword" />
                        <label for="password2">Re-Password</label>
                    </div>
                </div>
                <div class="row" v-show="feedback">
                    <div class="col s12">
                        <p class="red-text" v-show="feedback">{{ feedback }}</p>
                    </div>
                </div>
                <button class="btn btn-large teal white-text">Login</button>
            </form>
        </div>
    </div>
</template>

<script>
// import firebase from "firebase";
export default {
    name: "Register",
    data() {
        return {
            email: null,
            password: null,
            repassword: null,
            feedback: null,
        };
    },
    methods: {
        register() {
            if (this.email && this.password && this.repassword) {
                if (this.password === this.repassword) {
                    console.log(this.email, this.password, this.repassword);
                } else {
                    this.feedback = "Password are not similer.";
                }
            } else {
                this.feedback = "Fill The Form.";
            }
        },
    },
};
</script>
