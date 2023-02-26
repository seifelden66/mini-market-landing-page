<template lang="pug">
Nav
.search 
  h3 search for products
  input(type="text" v-model="input")
.main(v-if="input === ''")
  Card(:data="data")
.main(v-else)
  FoundProduct(:data="data" :input="input")
</template>


<script lang="ts" setup>
const input = ref<string | undefined>("");

const { data } = await useAsyncGql(
  "products",
  reactive<{ name: string | undefined }>({ name: "" })
)



</script>

<style lang="scss">

.search{
  background-color: rgba(139, 133, 224, 0.726);
  margin: -8px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  input{
    height: 25px;
    border-radius: 5px;
    border-style: none;
    background-color: rgba(37, 94, 145, 0.253);
  }
}
.main {
  margin: 15px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  .card {
    background-color: rgba(38, 76, 199, 0.5827);
    padding: 10px;
    display: grid;
    justify-items: center;
    align-items: center;
    #link{
      text-decoration: none;
      color: white;
    }
    img {
      width: 100%;
      height: 220px;
      transition: 300ms;
      &:hover {
        transform: scale(1.05);
      }
    }
  }
}
@media (max-width: 1024px) {

  .search{
    
    margin: -8px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1rem;
    input{
      height: 20px;
      border-radius: 5px;
      border-style: none;
      background-color: rgba(37, 94, 145, 0.253);
    }
  }
  .main {
    font-size: small;
    margin-top: 15px;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 0.5rem;
    .card {
      padding: 5px;

      img {
        width: 120px;
        height: 90px;
        transition: 300ms;
        &:hover {
          transform: scale(1.1);
        }
      }
    }
  }
}
</style>
