<template>
  <h1>Актуальные новости: </h1>
  <span>Открыто: {{openRate}} || Просмотрено: {{readRate}}</span>  
  <app-news 
    v-for="item in news" 
    :key="item" 
    :title="item.title" 
    :text="item.text" 
    :isOpen="item.isOpen" 
    :wasRead="item.wasRead"
    :id="item.id"
    @open-news="openNews"
    @read-news="readNews"
  />
  <div>
    <h1 v-for="title in arr" :key="title">{{title}}</h1>
  </div>
</template>

<script>
import AppNews from './components/AppNews.vue'
  export default{
    name: 'App',
    data(){
      return{
        openRate: 0,
        readRate: 0,
        news:[
          {title: 'News1', isOpen: false, wasRead: false, id: 1, text: 'text1'},
          {title: 'News2', isOpen: false, wasRead: false, id: 2, text: 'text2'},
          {title: 'News3', isOpen: false, wasRead: false, id: 3, text: 'text3'}
        ]
      }
    },
    components:{
      'app-news': AppNews
    },
    methods:{
      openNews(){
        this.openRate++
      },
      readNews(id){
        let idx = this.news.findIndex(news => news.id === id)
        this.news[idx].wasRead = false 
        this.readRate++
      },

    }
  }
</script>

<style>

</style>
