<template>
    <div class="home">
        <div class="welcome container">
            <div class="card">
                <h2 class="teal-text">Welcome</h2>
                <form action="" @submit.prevent="enterChat">
                    <label for="name">Enter your name: </label>
                    <input type="text" name="name" v-model="name" />
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
        };
    },
    components: {
        // HelloWorld
    },
    methods: {
        enterChat() {
            console.log(this.name);
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
