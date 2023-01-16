<template>
  <div>
    <p>{{noteText}}</p>
    <button @click="deleteNote">Удалить</button>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        inputVal: null,
        notes: ["Заметка 1", "Заметка 2"]
      }
    },
    methods:{
      addNote(val){
        this.notes.push(val)
      },
      deleteNote(){
        
      }
    },
    props:{
      noteText: String
    }
  }
</script>

<style>

</style>
