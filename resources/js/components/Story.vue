<template>
    <div class="story">
        <h2>{{ number }}. {{ title }} </h2>
        <p class="story__content" v-html="content"></p>
    </div>
</template>

<script>
export default {
    name: 'Story',
    props: {
        number: {
            type: String
        },
        title: {
            type: String
        },
        content: {
            type: String
        }
    }
}
</script>


<style scoped lang="scss">
.story {
    margin-bottom: 20px;
}
</style>
