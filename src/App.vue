<template>
    <div id="root">
    <!-- <myheader></myheader> -->
    <searchbox id="sbox" v-on:on-child-updated="childUpdated"></searchbox>
    <showresult id="sresult" v-bind:search-value="parentValue"></showresult>
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
#root {
    width: 1080px;
    height: 800px;
    display: table;
    /* height: 500px; */
    /* padding-bottom: 100vh; */
    /* margin-bottom: 100vh; */
    margin: auto;
    background-color: #fff;
}

#sbox {
    position: fixed;
    width:250px;
    height: auto;
    /* display: inline-block; */
    display: table-cell;
    padding: 0;
    /* float: left; */
    /* border-right: solid 1px black; */
    background-color: #393a45;
}

#sresult {
    width:830px;
    height: auto;
    display: table-cell;
    padding: 0;
    /* display: inline-block; */
    /* border-left: solid 1px #51525C; */
    background-color: #fff;
}
</style>