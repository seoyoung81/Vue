<template>
  <h2>결정세액: 
    <span v-if="taxCalculation - taxReduction>=0">{{ taxCalculation - taxReduction }} </span>
    만원</h2>
</template>

<script>
export default {
    name: 'FinalTax',
    props: {
        taxCalculation: Number,
        taxReduction: Number
    }
}
</script>

<style>

</style>