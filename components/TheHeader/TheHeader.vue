<template>
<div>
    <vs-navbar v-model="indexActive" :color="colorx" text-color="rgba(255,255,255,.6)" active-text-color="rgba(255,255,255,1)" class="myNavbar text-white">
        <div slot="title">
            <vs-navbar-title>
                RECIPE BLOG
            </vs-navbar-title>
        </div>

        <vs-navbar-item index="0">
            <nuxt-link to="/">All posts</nuxt-link>
        </vs-navbar-item>

        <vs-navbar-item index="1">
            <nuxt-link to="/about">About</nuxt-link>
        </vs-navbar-item>

    </vs-navbar>

</div>
</template>

<script>
import Vue from "vue";
import Vuesax from "vuesax";
import "vuesax/dist/vuesax.css";
import "material-icons/iconfont/material-icons.css";
Vue.use(Vuesax);

export default {
    data: () => ({
        colorx: "#4d0c88",
        indexActive: 0
    })
};
</script>

<style>

</style>
