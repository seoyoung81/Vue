<template>
  <div>
    <p>연봉 입력 (만원): <input type="number" v-model.number="totalIncome"></p>
    <p>세액감면액 (만원): <input type="number" v-model.number="taxReduction"></p><hr>

    <h2>종합소득금액: {{ totalIncome }} 만원</h2>
    <h2>종합소득공제: (-) 150 만원</h2>
    <h2>과세표준: <span v-if="totalIncome>=150">{{ totalIncome - 150 }}</span>
        만원</h2><hr>
    <!-- <TaxRate/> -->
    <TaxRate :total-income="totalIncome" :tax-reduction="taxReduction"/>

  </div>
</template>

<script>
import TaxRate from '@/components/TaxRate.vue'

export default {
    name: 'MyIncome',
    components: {
        TaxRate,
    },
    data(){
        return {
            totalIncome: null,
            taxReduction: null,
        }
    }
    
}
</script>

<style>

</style>