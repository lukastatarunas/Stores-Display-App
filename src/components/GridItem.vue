<template>
<div class="grid">
    <div class="grid-item" v-for="store in stores" :key="store.code" @click="openStoreInfo(store)">
        {{ store.name }}
    </div>
</div>
</template>

<script>
export default {
    name: "GridItem",
    props: {
        stores: null
    },
    methods: {
        openStoreInfo(store) {
            this.$q.dialog({
                title: store.name,
                message: `Country Code: ${
          store.countryCode ? store.countryCode : "No Country Code."
        }
        State: ${store.state}.
        City: ${store.city}.
        Company Name: ${store.companyName}.
        Store Type: ${store.storeType}.
        Email: ${store.storeEmail ? store.storeEmail : "No Email."}
        Phone: ${store.storePhone}.
        Address: ${store.address}.
        Post Code: ${store.postCode}.
        Latitude: ${store.latitude}.
        Longitude: ${store.longitude}.
        Allowance: ${store.allowance}.
        ${store.openNow ? "Open Now!" : "Closed Now!"}`
            });
        }
    }
};
</script>

<style>
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(500px, 1fr));
    grid-gap: 30px;
    justify-items: center;
    align-items: center;
    padding: 35px;
    background-color: #000000;
    height: 100vh;
}

@media screen and (max-width: 1100px) {
    .grid {
        height: 150vh;
    }
}

.grid-item {
    background-color: #c52035;
    color: #ffffff;
    padding: 20px;
    cursor: pointer;
    font-weight: bold;
    width: 300px;
    text-align: center;
}
</style>
