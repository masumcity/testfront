<template>
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto">
      <div class="flex flex-wrap -m-4">
        <div v-for="product in products" :key="product.id" class="lg:w-1/4 md:w-1/2 p-4 w-full">
          <a class="block relative h-48 rounded overflow-hidden">
            <img
              alt="ecommerce"
              class="object-cover object-center w-full h-full block"
              :src=product.thumbnail
            />
          </a>
          <div class="mt-4">
            <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">
              {{product.category.name}}
            </h3>
            <h2 class="text-gray-900 title-font text-lg font-medium">
              {{product.name}}
            </h2>
            <p class="mt-1">{{product.api.retailprice}} TK</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "IndexPage",

  data(){
    return {
      products: null,
    }
  },

  created() {
    this.$axios
      .get("/api/brand/Remax")
      .then((res) => {
        console.log(res.data);
        this.products = res.data.data;
      });
  },
};
</script>
