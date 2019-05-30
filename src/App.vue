<template>
    <div id="root">
    <!-- <myheader></myheader> -->
    <searchbox id="sbox" v-on:on-child-updated="childUpdated"></searchbox>
    <showresult id="sresult" v-bind:search-value="parentValue"></showresult>
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
    // コンポーネント間通信（検索ワードを通信）
    data () {
        return {
            parentValue: "海 風景"
        }
    },
    methods: {
        childUpdated(v) {
            this.parentValue = v;
        }
    },
}
</script>

<style>
#root{
    width: 1080px;
    margin: auto;
}

#sbox{
    width:250px;
    height: 1000px;
    display: inline-block;
    float: left;
    /* border-right: solid 1px black; */
    background-color: #393a45;
}

#sresult{
    width:830px;
    height: 1000px;
    display: inline-block;
    background-color: #2e2e34;
}
</style>