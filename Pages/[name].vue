<template lang="pug">
Nav
div.det(v-for="item in data.products.items" :key="item.name")
  div(v-if="item.name === namee")
    h1 {{ item.name }}
    img(:src="item.featuredAsset.source" alt="image")
    h4 {{ item.description }}
    button(@click="add") add
  
</template>

<script setup lang="ts">
const route = useRoute();
const namee = route.params.name;
const { data } = await useAsyncGql(
  "products",
  reactive<{ name: string | undefined }>({ name: "" })
);
</script>
<style lang="scss">
.det {
    padding: 10px;
    
    img {
        margin: 5px;
        width: 250px;
        height: 200px;
    }
}
@media (max-width: 1024px) {
    .det {
        margin-left: 20px;
        img {
            margin: 10px;
            width: 220px;
            height: 200px;
        }
    }
}
</style>
