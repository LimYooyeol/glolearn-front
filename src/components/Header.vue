<template>
<div>
  <b-navbar class="temp" toggleable="lg" type="dark">
    <b-navbar-brand>
        <router-link to="/">
            <img style = "width:80%" src="@/assets/GLL_logo.png">
        </router-link>
    </b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item class = "menu" href="#">강의</b-nav-item>
        <b-nav-item class = "menu">
            <router-link to="/about">강의실</router-link>
        </b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ms-auto">
        <div v-if="authed">
            <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template #button-content>
                <em>{{nickname}} 님</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown>
        </div>
        <div v-else>
            <b-nav-item>
                <router-link to="/login">로그인</router-link>
            </b-nav-item>
        </div>
      </b-navbar-nav>

    </b-collapse>
  </b-navbar>
</div>
</template>
<script>
import axios from 'axios'
export default{ 
    name:[],
    components:{},
    data(){
        return{
            nickname:'로그인',
            authed: false,
        };
    },
    setup(){},
    created(){

    },
    mounted(){},
    unmounted(){},
    methods:{}
}
</script>
<style scoped>
    .temp{
        padding-left: 5%;
        padding-right: 5%;
        margin-top: 10px;
        font-size: 1.5em;
        border-bottom: 1px solid;
        border-color: lightgrey;
    }

    .menu{
        padding-left:40px;
        padding-right:40px;
    }

    a{
        text-decoration:none;
        font-weight: normal;
        color:black;
    }

    .router-link-active {
        color: black;
        font-weight: bold;
    }

</style>