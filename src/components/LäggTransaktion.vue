<template>
  <h3>Lägg till ny transaktion</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Beskrivning av saken:</label>
      <input
        type="text"
        id="text"
        placeholder="Beskriv din köp"
        v-model="text"
      />
    </div>
    <div class="form-control">
      <label for="amount"
        >Belopp <br />
        (negativ - kostnad, positiv - inkomst,skuld till dig och till
        andra)</label
      >
      <input
        type="text"
        id="amount"
        placeholder="skriv beloppet i kronor här"
        v-model="amount"
      />
    </div>
    <button class="btn">Lägg till transaktion</button>
  </form>
</template>

<script setup>
import { useToast } from "vue-toastification";
import { ref } from "vue";

const text = ref("");
const amount = ref("");

const toast = useToast();

const emit = defineEmits(["transactionSubmitted"]);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("Båda fälten måste fyllas i.");
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmitted", transactionData);

  text.value = "";
  amount.value = "";
};
</script>
