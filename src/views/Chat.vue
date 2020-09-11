<template>
    <div class="chat container">
        <h2 class="center teal-text">GeoChat</h2>
        <div class="card">
            <div class="card-content">
                <ul class="messages" v-chat-scroll>
                    <li v-for="message in messages" :key="message.id">
                        <span class="teal-text"> {{ message.name }}: </span>
                        <span class="grey-text text-darken"> {{ message.content }} </span>
                        <br />
                        <span class="grey-text time"> {{ message.timestamp }}</span>
                    </li>
                </ul>
                <div class="card-action">
                    <NewMessage :name="name" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import NewMessage from "@/components/NewMessage.vue";
import db from "@/firebase/init";
import moment from "moment";

export default {
    name: "Chat",
    props: ["name"],
    components: {
        NewMessage,
    },
    data() {
        return {
            messages: [],
        };
    },
    created() {
        let ref = db.collection("messages").orderBy("timestamp");
        ref.onSnapshot((snapshot) => {
            let changes = snapshot.docChanges();
            changes.forEach((change) => {
                if (change.type == "added") {
                    let doc = change.doc;
                    this.messages.push({
                        id: doc.id,
                        name: doc.data().name,
                        content: doc.data().content,
                        timestamp: moment(doc.data().timestamp).format("lll"),
                    });
                }
            });
        });
    },
};
</script>

<style>
.chat h2 {
    font-size: 2.6em;
    margin-bottom: 40px;
}
.chat span {
    font-size: 1.4em;
}
.chat .time {
    display: block;
    font-size: 1.1em;
}
.messages {
    max-height: 300px;
    overflow: auto;
}
.messages::-webkit-scrollbar {
    width: 2px;
}
.messages::-webkit-scrollbar-track {
    background: #ddd;
}
.messages::-webkit-scrollbar-thumb {
    background: #aaa;
}
</style>
