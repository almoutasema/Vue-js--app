<template>
  <h4>Hela Beloppet</h4>
  <h1 id="balance">kr{{ total }}</h1>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
