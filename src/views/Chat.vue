<template>
    <div class="chat container">
        <h2 class="center teal-text">GeoChat</h2>
        <div class="card">
            <div class="card-content">
                <ul class="messages">
                    <li>
                        <span class="teal-text">Name: </span>
                        <span class="grey-text text-darken">Messages: </span>
                        <span class="grey-text time">Time: </span>
                    </li>
                </ul>
                <div class="card-action">
                <NewMessage  :name="name" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import NewMessage from "@/components/NewMessage.vue";
export default {
    name: "Chat",
    props: ["name"],
    components: {
        NewMessage,
    },
    data() {
        return {};
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
.chat time {
    display: block;
    font-size: 1.2em;
}
</style>
