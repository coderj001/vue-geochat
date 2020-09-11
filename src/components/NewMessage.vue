<template>
    <div class="new-messages">
        <form action="" @submit.prevent="addMessage">
            <label for="new-messages">New Messages (enter to add): </label>
            <p class="red-text" v-show="feedback">{{ feedback }}</p>
            <div class="input-field">
                <i class="material-icons prefix">textsms</i>
                <input type="text" name="new-message" v-model="newMessage" />
            </div>
        </form>
    </div>
</template>

<script>
import db from "@/firebase/init";
export default {
    name: "NewMessage",
    props: ["name"],
    data() {
        return {
            newMessage: null,
            feedback: null,
        };
    },
    methods: {
        addMessage() {
            if (this.newMessage) {
                db.collection("messages")
                    .add({
                        content: this.newMessage,
                        name: this.name,
                        timestamp: Date.now(),
                    })
                    .catch(() => {
                        console.log("Error");
                    });
                this.newMessage = null;
                this.feedback = null;
            } else {
                this.feedback = "Please enter some message.";
            }
        },
    },
};
</script>

<style scoped></style>
