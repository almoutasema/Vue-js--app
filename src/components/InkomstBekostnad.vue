<template>
  <div class="inc-exp-container">
    <div>
      <h4>Inkomst</h4>
      <p id="money-plus" class="money plus">+kr{{ income }}</p>
    </div>
    <div>
      <h4>Bekostnad</h4>
      <p id="money-minus" class="money minus">-kr{{ expenses }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>
