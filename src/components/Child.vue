<script>
export default {
    components: {

    },
    props: ["text", "amount"],
    methods: {
        changeColor() {
            this.$emit("color")
        },
    },
}

</script>
<template>
    <div class="child">
        <p class="child-1">{{ text }}</p>
        <p class="child-2">{{ amount }}</p>
    </div>
</template>
<style lang="scss" scoped>
.child {
    display: flex;
    justify-content: space-between;
    border: 2px solid rgb(88, 155, 227);
    font-weight: bold;
    font-size: 22px;
    margin-top: 20px;
    border-radius: 20px;
    width: 400px;

    .child-1 {
        padding-left: 20px;
        color: rgb(88, 155, 227);
    }

    .child-2 {
        padding-right: 20px;
    }
}
</style>