<script>
export default {
    name: "CharacterCard",
    props: {
        info: Object
    }
}
</script>

<template>
    <div class="card-wrapper">
        <div class="card">
            <h2>{{ info.name }}</h2>
            <h4>{{ info.origin.name }}</h4>
            <img :src="info.image" />
        </div>
    </div>
</template>

<style scoped>
.card-wrapper {
    padding: 1rem;
    width: 50%;
}

.card {
    padding: 1rem;
    background: orangered;
    color: white;
}

.card img {
    width: 100%;
}
</style>