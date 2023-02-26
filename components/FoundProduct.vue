<template lang="pug">
.card(v-for="item in data.products.items.filter((i) => i.name.toLowerCase().includes(input))" :key="item.name")
        img(:src="item.featuredAsset.source")
        h2 {{ item.name }}
        .down
                NuxtLink#link(:to="`/${item.name}`") show details
                button add to cart
</template>


<script setup lang="ts">
const props = defineProps(['data', 'input']);
</script>