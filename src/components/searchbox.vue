<template>
    <div id="searchbox">
        <input class="search" type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        <div> 
            F値：
            <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
            {{num}}
        </div>
        <button class="search-button" @click="search()">検索</button>
    </div>
</template>

<script>
export default {
    data () {
        return {
            num: '0',
        }
    },
    methods: {
        search () {
            // flicker apiで検索して結果を返す
            this.msg = ''
        },
    },
}
</script>

<style>
#searchbox{
    border: double 5px blue;
    text-align: center;
}

.search{
    width: 50%;
}

.search-button{
    margin: auto;
}
</style>
