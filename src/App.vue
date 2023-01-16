<template>
  <h1>Актуальные новости: {{now}} {{time}}</h1>
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
    @unread-news="unReadNews"
  />
  <todo-list
    v-for="item in news" 
    :key="item"
    :note-text="item.title"
  />

</template>

<script>
import AppNews from './components/AppNews.vue'
import TodoList from './components/TodoList.vue'

  export default{
    name: 'App',
    data(){
      return{
        openRate: 0,
        readRate: 0,
        now: new Date().toLocaleDateString(),
        time: null,
        news:[
          {title: 'News1', isOpen: false, wasRead: false, id: 1, text: 'text1'},
          {title: 'News2', isOpen: false, wasRead: false, id: 2, text: 'text2'},
          {title: 'News3', isOpen: false, wasRead: false, id: 3, text: 'text3'}
        ]
      }
    },
    mounted(){
      this.now = new Date().toLocaleTimeString()
    },
    components:{
      'app-news': AppNews,
      'todo-list': TodoList
    },
    methods:{
      openNews(){
        this.openRate++
      },
      readNews(id){
        let idx = this.news.findIndex(news => news.id === id)
        this.news[idx].wasRead = true 
        this.readRate++
      },
      unReadNews(id){
        let idx = this.news.findIndex(news => news.id === id)
        this.news[idx].wasRead = false 
        this.readRate--
      }
    }
  }
</script>

<style>

</style>
