<script>
export default {
    data() {
        return {

        };
    },
    methods: {},
    components: {},
    props:{
        singlecard: Object
    }

}
</script>

<template>
    <div class="card">
        <img :src="singlecard.card_images[0].image_url" class="card-img-top" alt="" />
    <div class="card-body">    
        <p class="card-text">
            {{ singlecard.name }}
        </p>
        <h3 class="card-title">
            {{ singlecard.archetype }}
        </h3>
    </div>
    </div>
</template>

<style lang="scss" scoped>
</style>
