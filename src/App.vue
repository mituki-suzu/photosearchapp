<template>
    <div>
    <myheader></myheader>
    <searchbox></searchbox>
    <showresult></showresult>
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