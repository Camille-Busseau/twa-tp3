<template>
    <!-- Section-->
    <section class="py-5">
        <div class="container px-4 px-lg-5 mt-5">
            <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                <div v-for="(product, i) in inventory" :key="i" class="col mb-5">
                    <div class="card h-100">
                        <!-- Product image-->
                        <img class="card-img-top" :src="require(`@/assets/img/450/${product.photo}`)" alt="..." />
                        <!-- Product details-->
                        <div class="card-body p-4">
                            <div class="text-center">
                                <!-- Product name-->
                                <h5 class="fw-bolder">{{ product.name }}</h5>
                                <!-- Product price-->
                                ${{ product.price.toFixed(2) }}
                            </div>
                            <span>{{ product.type }}</span>
                        </div>
                        <!-- Product actions-->
                        <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                            <div class="text-center">
                                <input type="number" class="form-control qt" v-model.number="product.quantity">
                                <div class="d-flex flex-column row-gap-2">
                                    <a class="btn btn-outline-dark mt-auto" @click="add(product.name, i)">Add to the
                                        cart</a>

                                    <RouterLink :to="{ name: 'product', params: { id: product.name } }">
                                        <a class="btn btn-outline-dark mt-auto link-offset-2 link-underline-opacity-25 link-underline-opacity-100-hover">Details</a>
                                    </RouterLink>

                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
  props: ['inventory', 'add']
}
</script>
