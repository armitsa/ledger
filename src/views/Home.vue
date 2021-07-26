<template>
  <div class="home">
    <ledger-input></ledger-input>
    <ledger-table></ledger-table>
  </div>
</template>

<script>
import LedgerInput from '@/components/LedgerInput.vue'
import LedgerTable from '@/components/LedgerTable.vue'
export default {
  name: 'Home',
  components: {
    LedgerInput,
    LedgerTable,
  }

}
</script>

<style>

</style>