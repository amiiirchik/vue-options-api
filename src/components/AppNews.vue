<template>
    <div>
        <h3>{{title}}</h3>
        <AppButton @click="openNews">{{isOpenNews ? "Закрыть" : "Открыть"}}</AppButton>
        <p v-if="isOpenNews">{{text}}</p>
        <AppButton v-if="!wasRead" @click="readNews()">Прочитано</AppButton>
        <AppButton v-if="wasRead" @click="unReadNews()">Не прочитано</AppButton>
        <hr>
    </div>
</template>
  
<script>
import AppButton from './AppButton.vue'

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
        emits: ['open-news', 'read-news', 'unread-news'],
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
                this.$emit('unread-news', this.id)
            }
        },
        components: {AppButton}
    }
</script>
