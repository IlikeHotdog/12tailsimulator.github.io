<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const nbLuck = ref<number>(0)
const nbWeaponEffect = ref<number>(0)
const nbHatEffect = ref<number>(0)
const nbArmorEffect = ref<number>(0)
const isCamelon = ref<boolean>(false)
// const multiple = ref<number>(1)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <input class="border" type="number" v-model="nbLuck" />
    <input class="border" type="number" v-model="nbWeaponEffect" />
    <input class="border" type="number" v-model="nbHatEffect" />
    <input class="border" type="number" v-model="nbArmorEffect" />
  </div>

  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
