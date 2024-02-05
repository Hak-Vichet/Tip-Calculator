<template>
  <!-- <div class="absolute flex flex-col items-center justify-center w-[500px] mt-[15%]">
    <h1 class="text-3xl text-green-900 mb-2">SPLI</h1>
    <h1 class="text-3xl text-green-900 mb-2">TTER</h1>
  </div> -->
  <div class="flex items-center justify-center blue-color h-screen p-10">
    <div class="w-[500px] bg-white rounded-2xl mt-3">
      <div class="grid md:grid-cols-2 w-full p-5">
        <!-- Left side  -->
        <div class="pr-3 p-2">
          <p class="text-xs text-gray-500">Bill</p>
          <div
            class="flex justify-between bg-gray-300/30 rounded-md py-1 px-2 focus:border-green-400"
          >
            <p class="text-sm text-gray-400">$</p>
            <div
              contenteditable
              @input="updateTextBill"
              class="outline-none"
              @keydown.enter.prevent="submitTextBill"
            >
              {{ billAmount }}
            </div>
          </div>

          <p class="text-xs text-gray-500 mt-5">Select Tip %</p>
          <div
            class="w-full flex flex-wrap gap-3 items-center justify-center text-center mt-1"
          >
            <div
              v-for="(num, index) in percentages"
              :key="index"
              class="w-[60px]"
            >
              <div
                @click="selectPercentage(num.id)"

                class="bg-green-800 rounded-md cursor-pointer"
              >
                {{ num.value }}
              </div>
            </div>
          </div>

          <p class="text-xs text-gray-500 mt-5">Number of People</p>
          <div class="flex justify-between bg-gray-300/30 rounded-md py-1 px-2">
            <p class="text-sm text-gray-400">$</p>
            <div
              contenteditable
              @input="updateTextPeople"
              @keydown.enter.prevent="submitTextPeople"
              data-inputmode="numeric"
              data-placeholder="0"
              class="text-sm outline-none"
            >
              {{ peopleNumber }}
            </div>
          </div>
          <p v-if="isError" class="text-red-500 text-sm">
            Please enter a valid number
          </p>
        </div>

        <!-- Right side  -->
        <div class="mt-5">
          <div
            class="bg-green-800 h-full flex flex-col rounded-lg p-3 space-y-3 pb-5"
          >
            <div class="flex justify-between items-center">
              <p class="text-xs text-white">Tip Amount</p>
              <h1 v-if="checkActions" class="text-2xl text-green-500">
                ${{ TipAmount }}
              </h1>
              <h1 v-else class="text-2xl text-green-500">${{ "0" }}</h1>
            </div>
            <div class="flex justify-between items-center">
              <p class="text-xs text-white">Total</p>
              <h1 v-if="checkActions" class="text-2xl text-green-500">
                ${{ totalPrice }}
              </h1>
              <h1 v-else class="text-2xl text-green-500">${{ "0" }}</h1>
            </div>

            <div class="flex flex-1"></div>

            <button
              class="bg-green-500 w-full items-center justify-center rounded-md text-sm py-1"
            >
              RESET
            </button>

            {{ selectedPercentage }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const percentages = [
  { id: 1, value: 5 },
  { id: 2, value: 10 },
  { id: 3, value: 15 },
  { id: 4, value: 25 },
  { id: 5, value: 50 },
  { id: 6, value: "Custom" },
];

const billAmount = ref(1);
const peopleNumber = ref(1);
const TipAmount = ref(1);
const totalPrice = ref(1);

const isSelected = ref(false);

const selectedPercentage = ref("");
const disabledPercentages =ref([])

const checkActions = ref(false);

const isError = ref(false);

watch(
  () => TipAmount.value,
  () => {
    checkActions.value = true;
  }
);

const updateTextBill = (event) => {
  billAmount.value = event.target.innerText;
};

const updateTextPeople = (event) => {
  peopleNumber.value = event.target.textContent.trim();
  const inputValue = event.target.textContent.trim();
  if (/^\d+$/.test(inputValue)) {
    peopleNumber.value = inputValue;
    isError.value = false;
  } else {
    isError.value = true;
  }
};

const submitTextBill = () => {
  calculateTipAmount();
};

const submitTextPeople = () => {
  if (!peopleNumber.value) {
    isError = true;
  }
  calculateTotalPrice();
};

const calculateTipAmount = () => {
  TipAmount.value = billAmount.value * peopleNumber.value;
};

const calculateTotalPrice = () => {
  totalPrice.value = billAmount.value * peopleNumber.value * selectedPercentage.value;
};

const selectPercentage = (id) => {
  selectedPercentage.value = percentages[id - 1].value;
  console.log("Percentage value: ", selectedPercentage.value);

    if (selectedPercentage.value !== null) {
      disabledPercentages.value = disabledPercentages.value.filter(
        (disabledPercentage) => disabledPercentage !== selectedPercentage.value
      );
    }

    disabledPercentages.value.push(percentages[id-1].value);
    console.log("Pushed: ", disabledPercentages.value);
};

</script>

<style scoped>
.blue-color {
  background-color: hsl(185, 39%, 82%);
}
</style>
