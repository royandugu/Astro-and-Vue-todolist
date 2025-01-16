<script>
    import { menu } from '../../data/menu';
</script>
<template>
    <ul>
        <li v-for="(item, index) in menu" :key="index">
            <a :href="item.link">{{ item.name }}</a>
        </li>
    </ul>
</template>
<style>

</style> 