<template>
  <main class="min-h-screen bg-gray-100">
    <div class="container py-6">
      <div class="p-4 bg-white shadow rounded">
        <!-- Quran Header -->
        <QuranHeader
          :surah="surah"
          :all-surah="allSurah"
          :getSpecificSurah="getSpecificSurah"
        />

        <!-- Loading Component -->
        <Loading v-if="loading" />

        <!-- Surah Ayah -->
        <Ayahs v-else :surah="surah" />
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Loading from "./components/Loading.vue";
import Ayahs from "./components/Ayahs.vue";
import QuranHeader from "./components/QuranHeader.vue";
export default {
  name: "App",
  methods: {
    selectedSurah(surahNum) {
      this.loading = true;
      axios
        .get("https://api.alquran.cloud/v1/surah/" + surahNum)
        .then((response) => {
          this.surah = response.data.data;
          this.loading = false;
        });
    },
    getSpecificSurah(e) {
      this.selectedSurah(e.target.value);
    },
  },
  data() {
    return {
      allSurah: [],
      surah: {},
      loading: true,
    };
  },
  mounted() {
    axios.get("https://api.alquran.cloud/v1/surah").then((response) => {
      this.allSurah = response.data.data;
    });
    this.selectedSurah(1);
  },
  components: { Loading, Ayahs, QuranHeader },
};
</script>

<style scoped>
.container {
  max-width: 800px;
  @apply mx-auto;
}
</style>
