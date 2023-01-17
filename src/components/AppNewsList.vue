<template>
    <h3>Список всех новостей</h3>
    <ul>
        <li v-for="item in news" :key="item">
            {{ item.title }}
            <span v-if="item.wasRead">Вы уже читали это</span>
        </li>
    </ul>
</template>
  
<script>
export default {
    name: 'AppNewsList',
    inject: ['news', 'props']
}
</script>

<style scoped>
span{
    font-size: 12px;
    color: green;
}
</style>