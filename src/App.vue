<template>
  <div id="app">
    <h1>News application</h1>
    <hr>
    <paginate
            :page-count="9"
            :page-range="3"
            :margin-pages="2"
            :click-handler="clickCallback"
            :prev-text="'Prev'"
            :next-text="'Next'"
            :container-class="'pagination'"
            :page-class="'page-item'">
    </paginate>
    <FilterNews
      v-on:toggle-isColumn="toggleIsColumn"
      v-bind:isColumn="isColumn"
      v-on:changeNewsOnPage="changeNewsOnPage"
    />
    <Loader v-if="loading"/>
    <NewsList
            v-else-if="news.length"
      v-bind:news="news"
      v-bind:isColumn="isColumn"
    />
  </div>
</template>

<script>
  import Paginate from 'vuejs-paginate';
  import Loader from './components/Loader';
  import NewsList from '@/components/NewsList';
  import FilterNews from '@/components/FilterNews';
  export default {
    name: 'App',
    data() {
      return {
        news: [],
        isColumn: true,
        newsOnPage: 10,
        currentPage: 1,
        loading: true
      }

    },
    watch: {
      newsOnPage(val) {
        this.newsOnPage = val;
        this.clickCallback(this.currentPage)
      }
    },
    mounted() {
      this.getNewsFromApi();
    },
    methods: {
      toggleIsColumn() {
         this.isColumn = !this.isColumn;
      },
      changeNewsOnPage(num) {
        this.newsOnPage = num;
      },
      getNewsFromApi() {
        this.loading = true;
        fetch(`http://jsonplaceholder.typicode.com/posts?_start=${this.currentPage}0&_limit=${this.newsOnPage}`)
          .then(response => response.json())
          .then(json => {
            setTimeout(() => {
              this.news = json
              this.loading = false
            }, 1000)
          })
      },
      clickCallback(num) {
        this.currentPage = num;
        this.getNewsFromApi();
      }
    },
    components: {
      NewsList,
      FilterNews,
      Paginate,
      Loader
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.pagination {
  display: flex;
  width: 100%;
  text-align: center;
  justify-content: center;
}

.pagination li{
  padding: 7px;
  border: 1px solid #ccc;
  border-radius: 3px;
  margin: 3px;
}

.disabled {
   display: none;
}

.active {
  background-color: #839ecc;
}

  ul, li {
    padding: 0;
    margin: 0;
    display: block;
  }
</style>
