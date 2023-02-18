<template>
    <div>
        <img src="https://k.kakaocdn.net/14/dn/btroDszwNrM/I6efHub1SN5KCJqLm1Ovx1/o.jpg" @click="loginWithKakao"
        style="cursor:pointer;" alt="카카오 로그인 버튼" />
    </div>
    </template>
    <script>
    import axios from 'axios';
    
    export default{ 
        name: [],
        components:{},
        data(){
            return{
                testMsg: ''
            };
        },
        setup(){},
        created(){
            axios.get('/api/test').then(
                res => {
                    this.testMsg = res.data;
                }
            )
        },
        mounted(){},
        unmounted(){},
        methods:{
            loginWithKakao() {
                const url = new URL(document.location.href)

                try{
                    window.Kakao.init('39820925f96876b00bbdc22a850605f9')  
                }catch(err){
                    console.log(err)
                }
    
                try{
                    window.Kakao.Auth.authorize({
                        redirectUri: 'http://localhost:8080/authentication?redirectUri=' + url.searchParams('redirectUri'),
                    });
                }catch(err){
                    console.log(err);
                }
    
            }
        }
    }
    </script>