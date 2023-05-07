<template>
  <div>
    <h2>산출세액: 
        <span v-if="taxCaculation()>=0">{{ taxCaculation() }}</span>
    만원</h2>
    <h2>세액감면: (-){{ taxReduction }} 만원</h2>
    <hr>
    <FinalTax :tax-calculation="taxCaculation()" :tax-reduction="taxReduction"/>
  </div>
</template>

<script>
import FinalTax from '@/components/FinalTax.vue'
export default {
    name: 'TaxRate',
    components: {
        FinalTax,
    },
    props: {
        taxReduction: Number,
        totalIncome: Number,
    },
    methods: {
        taxCaculation (){
            const taxBase = this.totalIncome - 150
            //가져다 사용합시다 !
            if (taxBase <= 1200) {
            return Math.round(taxBase * 0.06)
            } else if (taxBase > 1200 && taxBase <= 4600) {
            return Math.round(taxBase * 0.15 - 108)
            } else if (taxBase > 4600 && taxBase <= 8800) {
            return Math.round(taxBase * 0.24 - 522)
            } else if (taxBase > 8800 && taxBase <= 15000) {
            return Math.round(taxBase * 0.35 - 1490)
            } else if (taxBase > 15000 && taxBase <= 30000) {
            return Math.round(taxBase * 0.38 - 1940)
            } else if (taxBase > 30000 && taxBase <= 50000) {
            return Math.round(taxBase * 0.4 - 2540)
            } else if (taxBase > 50000 && taxBase <= 100000) {
            return Math.round(taxBase * 0.42 - 3540)
            } else {
            return Math.round(taxBase * 0.45 - 6540)
            }
        }
    }
    
}
</script>

<style>

</style>