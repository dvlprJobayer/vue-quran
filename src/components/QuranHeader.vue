<template>
  <div class="flex items-center">
    <!-- Select Surah -->
    <div class="flex-[2]">
      <select @change="getSpecificSurah" class="quran-input">
        <option
          v-for="surah in allSurah"
          :key="surah.number"
          :value="surah.number"
        >
          {{ surah.name }} - {{ surah.englishName }}
        </option>
      </select>
    </div>
    <!-- Surah Name -->
    <div class="flex-[2] flex flex-col items-center">
      <h3 class="font-bold text-lg">
        {{ surah.name }} - {{ surah.englishName }}
      </h3>
      <p>{{ surah.englishNameTranslation }}</p>
    </div>
    <!-- Surah additional info -->
    <div class="flex-1">
      <h4 class="font-bold text-center">{{ surah.revelationType }}</h4>
      <p class="text-center">Ayah: {{ surah.numberOfAyahs }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuranHeader",
  props: {
    surah: {
      type: Object,
      required: true,
    },
    allSurah: {
      type: Array,
      required: true,
    },
    getSpecificSurah: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped>
.quran-input {
  @apply border border-gray-300 px-4 py-2 rounded w-full;
}
</style>
