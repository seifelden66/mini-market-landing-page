<template lang="pug">
.card(v-for="item in data.products.items" :key="item.name")
    img(:src="item.featuredAsset.source")    
    h2 {{ item.name }}
    .down
        NuxtLink#link(:to="`/${item.name}`") show details
        button(@click="update" ) add to cart 
        
</template>

<script setup lang="ts">
const props = defineProps(['data']);
const cart = useCart()
const update = ()=> cart.value =cart.value+1
</script>
<style lang="scss">
.down{
    display: flex;
    align-items: center;
    gap: 0.5rem;
    button{
        padding: 6px;
        border-radius: 5px;
        border-style: none;
        transition: 300ms;
        &:hover{
            background-color: rgba(255, 228, 196, 0.726);
            padding: 6.25px;
            cursor: pointer;
        }
    }
}
</style>
