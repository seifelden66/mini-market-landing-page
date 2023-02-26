<template>
<div class="card" v-for="item in data.products
        .items.filter((i) =>
        i.name.toLowerCase().includes(input))"
        :key="item.name">

        <img :src="item.featuredAsset.source" alt="" />
        <h2>{{ item.name }}</h2>
        <NuxtLink :to="`/${item.name}`" id="link">show details</NuxtLink>
</div>
</template>

<script setup lang="ts">
const props = defineProps(['data', 'input']);
</script>