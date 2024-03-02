<template>
  <nav>
    <input />
    <div>
      <a href="#one"> Section 1 </a>
      <a href="#two"> Section 2 </a>
      <select @change="switchLang" name="lang" id="cars">
        <option
          v-for="item in dropdownOptions"
          :value="item.value"
          :key="item.value"
          :selected="item.value == currentLang"
        >
          {{ item.text }}
        </option>
      </select>
    </div>
  </nav>
</template>

<script setup lang="ts">
const switchLang = (event: Event) => {
  const target = event.target as HTMLSelectElement;
  if (target) emits("select", target.value);
};

const props = defineProps<{
  currentLang: string;
}>();
const emits = defineEmits(["select"]);

const dropdownOptions = [
  {
    value: "en",
    text: "English",
  },
  {
    value: "fr",
    text: "Française",
  },
  {
    value: "ru",
    text: "Русский",
  },
];
</script>

<style>
nav {
  padding: 30px 0;
  width: 100%;
  top: 0;
  left: 0;
  background: #000;
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

a {
  color: #fff;
  margin-right: 40px;
}
</style>
