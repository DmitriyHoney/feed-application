<template>
    <li class="news-item">
        <div class="news-image">
            <img :src="oneNews.img || `https://avatars.mds.yandex.net/get-pdb/2380153/85d417c7-8d83-4ca3-8abb-89032bc054a4/s1200`" alt="">
        </div>
        <div class="info">
            <h4>
                {{oneNews.title}}
            </h4>
            <p>
                {{oneNews.body}}
            </p>
        </div>
    </li>
</template>

<script>
    export default {
        props: {
            oneNews: {
                type: Object,
                required: true
            }
        },
    }
</script>

<style scope>
    .news-image {
        width: 250px;
        height: 200px;
        margin: 0px auto;
    }
    .news-image img {
        width: 100%;
        height: 100%;
    }

    .news-item {
        width: 300px;
        text-align: center;
        border: 1px solid #ccc;
        padding: 15px;
        border-radius: 3px;
        margin-top: 30px;
    }
</style>