<template>
<!-- このコンポーネントでは検索結果を表示する -->
    <div id="showresult">
        <p class="result" v-for="(post, id) in posts" :key="post.id">
            {{id}}.{{post.title}}
        </p>
    </div>
</template>

<script>
export default {
    data() {
        return{
            posts: [
            { id: 1, title: 'My journey with Vue' },
            { id: 2, title: 'Blogging with Vue' },
            { id: 3, title: 'Why Vue is so fun' }
            ],
        }
    },
}
</script>

<style>
#showresult{
}

.result{
    width: 30vw;
    height: 45vw;
    border: solid 1px red;
    float: left;
    margin-right: 2vw;
}
</style>
