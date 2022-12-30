<template>
  <div class="mt-4">
    <p
      v-for="ayah in surah.ayahs"
      :key="ayah.number"
      class="text-2xl flex items-center mb-4"
    >
      <span
        class="text-sm h-6 w-6 leading-6 inline-block text-center border rounded-full mr-2"
      >
        {{ ayah.numberInSurah }}
      </span>
      {{ ayah.text }}
    </p>
  </div>
</template>

<script>
export default {
  name: "Ayahs",
  props: {
    surah: {
      type: Object,
      required: true,
    },
  },
};
</script>
