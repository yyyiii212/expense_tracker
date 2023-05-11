<script>
export default {
    props: [],
    data() {
        return {
            sourceData: {
                text: ""
            },
        }
    },
    methods: {
        changeShow() {
            this.$emit("delswitch")
        },
        push() {
            this.changeShow();
            this.$emit("delemitpush", this.sourceData)
        },
    }
}
</script>
<template>
    <!-- 彈跳視窗 -->
    <div id="model" class="model">

        <!-- model card -->
        <div class="card">
            <p class="card-text">Text</p>
            <input id="text" type="text" v-model="sourceData.text">
            <button class="card-btn" type="button" @click="push">Delete transaction</button>
        </div>

        <!-- background -->
        <div class="bg"></div>
    </div>
</template>
<style lang="scss" scoped>
.model {
    width: 100vw;
    height: 100vh;
    // background-color: rgb(70, 76, 78);
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 2s;

    .card {
        width: 30vw;
        background-color: #fff;
        border-radius: 2rem;
        padding: 2rem;

        #text {
            margin-top: -20px;

        }

        #amount {
            margin-top: -20px;
        }

        .card-text {
            // margin-top: 10px;
            color: rgb(106, 170, 225);
        }

        .card-btn {
            margin-top: 20px;
            border-radius: 20px;
        }
    }

    .bg {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: black;
        opacity: 0.6;
        z-index: -1;
    }

}
</style>