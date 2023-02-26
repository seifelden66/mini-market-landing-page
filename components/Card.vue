<template >
    
    <div v-for="item in data.products.items" :key="item.name" class="card">
        <img :src="item.featuredAsset.source" alt="" />
        <h2>{{ item.name }}</h2>
        <NuxtLink :to="`/${item.name}`" id="link">show details</NuxtLink>
    </div>

</template>
<script setup lang="ts">
const props = defineProps(['data']);
</script>
