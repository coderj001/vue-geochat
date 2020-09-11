<template>
    <div class="new-messages">
        <form action="" @submit.prevent="addMessage">
            <label for="new-messages">New Messages (enter to add): </label>
            <input type="text" name="new-message"  v-model="newMessage"/>
        </form>
    </div>
</template>

<script>
export default {
    name: "NewMessage",
    props: ["name"],
    data() {
        return {
            newMessage: null,
        };
    },
    methods: {
        addMessage() {
                console.log(this.newMessage, this.name, Date.now())
            },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
