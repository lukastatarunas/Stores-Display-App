<template>
    <GridItem :stores="stores" />
</template>

<script>
import GridItem from "./GridItem";
export default {
    name: "Grid",
    components: {
        GridItem
    },
    data() {
        return {
            stores: []
        };
    },
    mounted() {
        this.fetchStores();
    },
    methods: {
        async fetchStores() {
            const response = await this.$axios.get(
                "https://demoapi.thedenstore.com/api/service?Request=Stores&Language=en-us"
            );
            this.stores = response.data;
        }
    }
};
</script>
