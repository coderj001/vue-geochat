<template>
    <div class="home">
        <div class="welcome container">
            <div class="card">
                <h2 class="teal-text">Welcome</h2>
                <form class="p" @submit.prevent="enterChat">
                    <label for="name">Enter your name: </label>
                    <input type="text" name="name" v-model="name" />
                    <p class="red-text" v-show="feedback">{{feedback}}</p>
                    <button class="btn teal">Enter Chat<i class="material-icons right">send</i></button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
    name: "Welcome",
    data() {
        return {
            name: null,
            feedback: null,
        };
    },
    components: {
        // HelloWorld
    },
    methods: {
        enterChat() {
            if ( this.name ){
                    this.$router.push({name: 'Chat', params: {name: this.name}})
                } else{
                        this.feedback="You Must Enter A Username."
                    }
        },
    },
};
</script>

<style>
.welcome {
    max-width: 400px;
    margin-top: 100px;
}
.welcome h2 {
    font-size: 3em;
}
.welcome button {
    margin: 30px auto;
}
</style>
