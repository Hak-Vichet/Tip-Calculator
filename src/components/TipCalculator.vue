<template>
    <div class="flex items-center justify-center blue-color h-screen p-10">
        <div class="max-w-xl bg-white rounded-2xl">
            <div class="grid md:grid-cols-2 w-full p-5">
                <!-- Left side  -->
                <div class="pr-3">
                    <p class="text-xs text-gray-500">Bill</p>
                    <div class="flex justify-between bg-gray-300/30 rounded-md py-1 px-2">
                        <p class="text-sm text-gray-400">$</p>
                        <p class="text-sm">$142.00</p>
                    </div>

                    <p class="text-xs text-gray-500 mt-5">Select Tip %</p>
                    <div class="grid grid-cols-3 text-center text-white text-sm gap-3 mt-2">
                        <div class="bg-green-900 rounded-sm py-1">5%</div> 
                        <div class="bg-green-900 rounded-sm py-1">10%</div>
                        <div class="bg-green-900 rounded-sm py-1">15%</div>
                        <div class="bg-green-900 rounded-sm py-1">25%</div>
                        <div class="bg-green-900 rounded-sm py-1">50%</div>
                        <div class="bg-green-900 rounded-sm py-1">Custom</div>
                    </div>

                    <p class="text-xs text-gray-500 mt-5">Number of People</p>
                    <div class="flex justify-between bg-gray-300/30 rounded-md py-1 px-2">
                        <p class="text-sm text-gray-400">$</p>
                        <p class="text-sm">$142.00</p>
                    </div>
                    
                </div>

                <!-- Right side  -->
                <div class="pl-3">
                    <div>askdjhsakdfhsa as fkhsdf kashdf ksa dfkas dhf</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup></script>

<style scoped>
.blue-color {
  background-color: hsl(185, 39%, 82%);
}
</style>
