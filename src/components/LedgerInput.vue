<template>
<div>
    <h1>Ledger</h1>

    <div>
        <div>
            <label for="date">Date :</label>
            <input type="text" v-model="form.date">
        </div>

        <div>
            <label for="explantation">Explantation :</label>
            <input type="text" v-model="form.explantation">
        </div>

        <div>
            <label for="amount">Amount :</label>
            <input type="text" v-model="form.amount">
        </div>

        <div>
            <button @click="addOrder(1)">Income</button>
            <button @click="addOrder(-1)">Expense</button>
        </div>

    </div>
</div>
</template>

<script>


import OrderStore from '@/store/Order'
export default {
    data() {
        return {
            type: 1,
            form: {
                date: '',
                explantation: '',
                amount:'',
            },
            balance: 4500
        }
    },
    methods: {
        clearForm() {
            this.form = {
                date: '',
                explantation: '',
                amount:'',
            }
        },
        addOrder(type) {
            this.type = type;
            console.log(type)
            
            if(this.type === -1){
                this.form.amount = (-1)*this.form.amount;
            }
            this.form.amount = Number(this.form.amount)
            this.balance = this.balance + this.form.amount

            let payload = {
                date: this.form.date,
                explantation: this.form.explantation,
                amount: this.form.amount,
                balance: this.balance
            }
            console.log(payload)
            OrderStore.dispatch("addOrder", payload)

            this.clearForm()
        },
    }
}
</script>

<style>

</style>