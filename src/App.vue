<template>
    <div>
    <myheader></myheader>
    <searchbox id="sbox"></searchbox>
    <showresult id="sresult"></showresult>
    <!-- <p v-if="msg.length > 0">
        {{msg}}
    </p> -->
    <!-- <p v-else>
        no text
    </p> -->
    <!-- <input type="text" placeholder="検索したいワードを入力してください" v-model="msg">
    <button @click="search()">検索</button> -->
    </div>
</template>

<script>
import myheader from './components/myheader'
import searchbox from './components/searchbox'
import showresult from './components/showresult'



export default {
    components: {
        myheader,
        searchbox,
        showresult,
    },
    // data () {
    //     return {
    //         msg: 'Hello World!!'
    //     }
    // },
    methods: {
        search () {
            // flicker apiで検索して結果を返す
            this.msg = ''
        }
    },
}
</script>

<style>
#sbox{
    width:14%;
    height: 90%;
    display: inline-block;
    float: left;
    border-right: solid 1px black;
    background-color: #8bc3f3;
}

#sresult{
    width:85%;
    height: 90%;
    display: inline-block;
    background-color: aliceblue;
}
</style>