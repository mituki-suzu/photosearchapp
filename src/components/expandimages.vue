<template>
    <transition>
        <div v-if="expand" class="image-table">
            <div id="table-left">
                <p id="image-title">
                    {{ imageTitle }}
                </p>
                <p id="image-url">
                    URL : {{ imageUrl }}
                </p>
                <!-- forでタグごとに表示 -->
                <button id="image-tag" v-for="tag in imageTag.split(' ')" :key="tag.id">
                    {{ tag }}
                </button>
            </div>
            <div id="table-right">
                <button class="close-button" @click="close()">Close</button>
                <img :src="imageUrl">
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    //親からURLとタグを受け取る
    props:[
        "imageTitle",
        "imageUrl",
        "imageTag",
        "imageId",
    ],
    data(){
        return{
            expand : false,
        }
    },
    methods:{
        close(){
            this.expand = false;
        },
    },
    watch: {
        // 親からデータを受け取るたびに実行
        imageUrl: function () {
            this.expand = true;            
        }
    },
}
</script>

<style>
#table-left {
    display: inline-block;
    width: 380px;
}

#table-left {
    display: inline-block;
    width: 700px;
}
.close-button {
    display: block;
    float: right;
    margin: 45px 50px 0 80vw;
}

.image-table {
    position: fixed;
    z-index: 2;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, .5);
    display: table;
    /* transition: opacity 1.0s ease; */
    color: white;
    text-align: center;
}

.image-table img {
    height: 60vh;
    /* margin-top: 50px; */
}

#image-title {
    font-family: 'Noto Sans CJK JP';
    font-size: 18px; 
    margin: 0;
}

#image-url {
    font-family: 'Noto Sans CJK JP';
    font-size: 12px; 
}

#image-tag {
    width: auto;
    height: 40px;
    border: solid 1px #fff;
    background-color: rgba(0, 0, 0, .5);
    color: #fff;
    border-radius: 5px;
    padding: 0 20px;
    margin-left: 10px;
}
</style>


