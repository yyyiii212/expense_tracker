<script>
import Popup from '../components/Popup.vue';
import Child from '../components/Child.vue';
import DelPopup from '../components/Popup-del.vue';
export default {
    components: {
        Popup,
        Child,
        DelPopup
    }
    , data() {
        return {
            status: {
                balance: parseInt(localStorage.getItem("balance")),
                income: parseInt(localStorage.getItem("income")),
                expense: -parseInt(localStorage.getItem("expense"))
            },
            account: localStorage.getItem("account"),
            delIsShow: false,
            num: 0,
            isTrue: false,
            isShow: false,
            modaInfo: [{
                text: "",
                amount: "",
            }]
        }
    },
    methods: {
        onEsc() {
            this.isShow = !this.isShow;
        },
        change() {
            this.isShow = !this.isShow;
        },
        delChange() {
            this.delIsShow = !this.delIsShow;
        },
        getPush(sourceData) {
            const vm = this;


            if (sourceData.text == "" || sourceData.amount == "") {
                vm.isTrue = false
            } else {
                if (vm.isTrue == false) {
                    vm.isTrue = !vm.isTrue;
                } if (vm.num == 0) {
                    vm.modaInfo[0].text = sourceData.text;
                    vm.modaInfo[0].amount = sourceData.amount;
                    vm.num = vm.num + 1;
                } else if (vm.modaInfo.length === 0) {
                    vm.modaInfo.push({ text: sourceData.text, amount: sourceData.amount });
                } else {
                    vm.modaInfo.push({ text: sourceData.text, amount: sourceData.amount });
                }
            }
            // vm.modaInfo.forEach(function (arr) {
            if (parseInt(sourceData.amount) >= 0) {
                vm.status.income += parseInt(sourceData.amount);
            } else {
                vm.status.expense += parseInt(sourceData.amount);
            }
            // })
            vm.status.balance = parseInt(vm.status.income) + parseInt(vm.status.expense);

        },
        deleteModaInfo(sourceData) {
            // 假設要刪除 text 為 "Breakfast" 的物件
            const index = this.modaInfo.findIndex(item => item.text === sourceData.text);
            if (index !== -1) {
                this.modaInfo.splice(index, 1);
            }

        }
    },
    mounted() {
    },
}
</script>
<template>
    <div class="page">
        <div class="page1">
            <div class="page1-content">
                <p>Expense Tracker</p>
                <div class="page1-content-1">
                    <p>{{ account }}</p>
                    <div class="balance">
                        <p>Your Balance</p>
                        <p>${{ status.balance }}</p>
                    </div>
                </div>
            </div>
        </div>
        <div class="page2">
            <div class="page2-1">
                <div class="income">
                    <p>INCOME</p>
                    <p>${{ status.income }}</p>
                </div>
                <div class="expense">
                    <p>EXPENSE</p>
                    <p>${{ status.expense }}</p>
                </div>
            </div>
            <div class="page2-2">
                <button id="add" type="button" @click="change">Add transaction</button>
                <button id="del" type="button" @click="delChange">Delete transaction</button>
                <Popup v-show="isShow" @emitpush="getPush" @switch="change" :sourceData.text="modaInfo.text"
                    :sourceData.amount="modaInfo.amount" />
                <DelPopup v-show="delIsShow" @delemitpush="deleteModaInfo" @delswitch="delChange" />
            </div>
            <div class="page2-3">
                <Child v-if="isTrue" v-for="card in modaInfo" :text="card.text" :amount="card.amount" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.page {
    width: 100vw;
    height: 100vh;
    display: flex;

    .page1 {
        width: 45%;
        height: 100%;
        background-color: rgb(128, 184, 234);
        display: flex;
        justify-content: center;
        font-weight: bold;

        .page1-content {
            height: 100%;
            padding-top: 100px;
            color: #fff;
            text-align: center;

            p {
                font-size: 38px;
            }
        }

        .page1-content-1 {
            padding-top: 180px;
            font-size: 28px;

            .balance {
                padding-top: 30px;
                font-size: 36px;
            }
        }
    }

    .page2 {
        width: 55%;
        display: flex;
        flex-direction: column;

        .page2-1 {
            width: 100%;
            display: flex;
            justify-content: space-evenly;
            padding-top: 80px;
            font-weight: bold;

            .income {
                font-size: 28px;
                color: rgb(77, 201, 129);
            }

            .expense {
                font-size: 28px;
                color: red;
            }
        }

        .page2-2 {
            width: 100%;
            padding-top: 60px;
            display: flex;
            justify-content: space-evenly;

            #add {
                width: 200px;
                height: 35px;
                background-color: rgb(99, 133, 219);
                border-radius: 10px;
                color: #fff;
            }

            #del {
                width: 200px;
                height: 35px;
                color: #fff;
                border-radius: 10px;
                background-color: rgb(156, 156, 162);

            }
        }

        .page2-3 {
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;

            .transaction {
                display: flex;
                justify-content: space-between;
                border: 2px solid rgb(88, 155, 227);
                font-weight: bold;
                font-size: 22px;
                margin-top: 20px;
                border-radius: 20px;
                width: 400px;

                .p1 {
                    padding-left: 20px;
                    color: rgb(88, 155, 227);
                }

                .p2 {
                    padding-right: 20px;
                    color: red;
                }

                .p3 {
                    padding-right: 20px;
                    color: rgb(94, 214, 102);
                }
            }
        }
    }
}
</style>