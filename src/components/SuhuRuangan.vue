<template>
  <div class="temperature-widget">
    <h2>Suhu Ruangan</h2>
    <div v-if="isLoading">
      <p>Mengambil data suhu...</p>
    </div>
    <div v-else>
      <p>Suhu saat ini: {{ temperature }}°C</p>
      <p v-if="isHighTemperature">Peringatan: Suhu terlalu tinggi!</p>
      <p v-else-if="isLowTemperature">Peringatan: Suhu terlalu rendah!</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      temperature: null,
      isLoading: true,
    };
  },
  mounted() {
    // Simulasi pengambilan data suhu dari server
    setTimeout(() => {
      this.temperature = this.getRandomTemperature();
      this.isLoading = false;
    }, 2000);
  },
  computed: {
    isHighTemperature() {
      return this.temperature > 28;
    },
    isLowTemperature() {
      return this.temperature < 18;
    },
  },
  methods: {
    getRandomTemperature() {
      // Simulasi suhu acak antara 15 dan 30 derajat Celsius
      return Math.floor(Math.random() * 16) + 15;
    },
  },
};
</script>

<style scoped>
.temperature-widget {
  border: 1px solid #ccc;
  padding: 20px;
  margin-bottom: 20px;
  text-align: center;
  background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.temperature-widget h2 {
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

.temperature-widget p {
  color: #666;
  font-size: 18px;
  margin-bottom: 10px;
}

.temperature-widget p.warning {
  color: red;
}
</style>
