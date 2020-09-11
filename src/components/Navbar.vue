<template>
    <nav>
        <div class="nav-wrapper teal">
            <div class="brand-logo"><router-link :to="{name: 'Welcome'}">GoeChat</router-link></div>
            <ul id="nav-mobile" class="right hide-on-med-and-down">
                <li><router-link :to="{name: 'Login'}">Login</router-link></li>
            </ul>
        </div>
    </nav>
</template>

<script>
export default {
    name: "Navbar",
    data() {
        return {};
    },
};
</script>
