<script setup>
import ShowLogo from "./components/ShowLogo.vue";
import { ref } from "vue";
const selectTab = ref(1);
const nbLuck = ref(0);
const nbWeaponEffect = ref(0);
const nbHatEffect = ref(0);
const nbArmorEffect = ref(0);
const isChameleon = ref(false);
const multiple = ref(1);
const WeaponEffectPercent = ref(0);
// const multiple = ref<number>(1)
function xcal() {
  if (isChameleon.value == true) {
    return (
      (nbWeaponEffect.value * multiple.value +
        nbHatEffect.value +
        nbArmorEffect.value) *
      (nbLuck.value / 100 + 1)
    );
  } else {
    return (
      (nbWeaponEffect.value * 1 + nbHatEffect.value + nbArmorEffect.value) *
      (nbLuck.value / 100 + 1)
    );
  }
  // return (nbWeaponEffect*.value+nbHatEffect+nbArmorEffect)*((nbLuck/100)+1);
  return 1;
}
function WeaponEffectPercentCal() {
  if (isChameleon.value == true) {
    return (
      (xcal() * 100) /
      (xcal() -
        (nbWeaponEffect.value * multiple.value +
          nbHatEffect.value +
          nbArmorEffect.value) +
        100)
    );
  } else {
    return (
      (xcal() * 100) /
      (xcal() -
        (nbWeaponEffect.value * 1 + nbHatEffect.value + nbArmorEffect.value) +
        100)
    );
  }
}
</script>

<template>
  <div class="flex justify-start align-top h-full w-full">
    <ShowLogo />
  </div>
  <select v-model="selectTab">
    <option value="1">คำนวณ ร้อยละ การเกิดผลพิเศษของอาวุธ</option>
    <option value="2">คำนวณค่าความเร็วของตัวละคร</option>
  </select>
  <div class="w-full flex flex-col items-center">
    <div class="flex flex-col w-[60%] pb-3" v-if="selectTab == 1">
      <label for>ค่า lck ทั้งหมดของตัวละคร</label>
      <input class="border" type="number" v-model="nbLuck" />
      <label for>ค่า Effect ของอาวุธ</label>
      <input class="border" type="number" v-model="nbWeaponEffect" />
      <label for>ค่า Effect ของหมวก</label>
      <input class="border" type="number" v-model="nbHatEffect" />
      <label for>ค่า Effect ของชุด</label>
      <input class="border" type="number" v-model="nbArmorEffect" />
      <label for>เป็นกิ่งก่าหรือไม่</label>
      <input class="border" type="checkbox"  v-model="isChameleon" />
      <select v-if="isChameleon" v-model="multiple">
        <option value="1">ไม่มีสกิลก่าสาย C</option>
        <option value="2">มีสกิลก่าสาย C</option>
      </select>
    </div>
    <div class="card border">
      <p>{{ WeaponEffectPercentCal() }}</p>
    </div>
  </div>
</template>
