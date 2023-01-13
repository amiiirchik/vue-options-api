<template>
    <div>
        <h3>{{title}}</h3>
        <button @click="openNews">{{isOpenNews ? "Закрыть" : "Открыть"}}</button>
        <p v-if="isOpenNews">{{text}}</p>
        <button @click="readNews">{{ wasReadNews ? "Не просмотрено" : "Просмотрено" }}</button>
        <hr>
    </div>
</template>
  
<script>
    export default{
        name: 'AppNews',
        data(){
            return{
                isOpenNews: this.isOpen,
                wasReadNews: this.wasRead
            }
        },
        props:{
            title: String,
            text: String,
            isOpen: Boolean,
            wasRead: Boolean,
            id: Number
        },
        emits: ['open-news', 'read-news'],
        methods: {
            openNews(){
                this.isOpenNews = !this.isOpenNews
                if(this.isOpenNews){                         //На открытие считает, на закрытие нет
                    this.$emit('open-news')
                }
            },
            readNews(){
                this.isOpenNews = false
                this.$emit('read-news', this.id)
            },
            unReadNews(){
                this.isOpenNews = true
                this.$emit('read-news', this.id)
            }
        }
    }
</script>
