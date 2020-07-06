<template>
    <ul class="news-wrap" v-bind:class="{col: isColumn}">
       <NewsItem
        v-for="oneNews of news"
        v-bind:oneNews="oneNews"
       />
    </ul>
</template>

<script>
    import NewsItem from '@/components/NewsItem';
    export default {
        props: ['news', 'isColumn'],
        components: {
            NewsItem
        }
    }
</script>

<style>
    .news-wrap {
        margin-top: 30px;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
    }
    .col {
        flex-direction: column;
    }
    .col li {
        width: 800px;
        padding: 5px;
        margin-bottom: 15px;
        display: flex;

        justify-content: flex-start;
    }
    .col li  div{
        margin: 0;
        margin-right: 15px;
    }
    .col .news-item {
        text-align: left;
    }
</style>