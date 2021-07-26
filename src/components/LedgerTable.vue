<template>
  <div>
      <table>
        <thead>
          <tr>
            <th> # </th>
            <th> Date </th>
            <th> Explantation </th>
            <th> Amount </th>
            <th> Balance </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(ord, index) in orders" :key="index">
            <td> {{ index+1 }} </td>
            <td> {{ ord.date }}</td>
            <td> {{ ord.explantation }} </td>
            <td> {{ ord.amount }}</td>
            <td> {{ ord.balance }}</td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>


import OrderStore from '@/store/Order.js'
export default {
  data() {
    return{
      orders: [],
      form: {
        date: '',
        explantation: '',
        amount: '',
      },
      balance:''
    } 
  },
  created() {
    this.fetchOrder()
  },
  methods:{
    fetchOrder(){
      OrderStore.dispatch('fetchData')
      this.orders = OrderStore.getters.orders
    },
  },
}
</script>

<style>

</style>