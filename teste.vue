<template>
   <q-layout>
    

    <q-page-container>
      <month-list />
      <q-page class="month-list-page">
        <q-card class="q-pa-md">
          <q-list bordered>
            <q-item v-for="(month, index) in months" :key="index" clickable @click="selectMonth(index)">
              <q-item-section>
                <q-item-label>{{ month }}</q-item-label>
              </q-item-section>
              <q-item-section side v-if="selectedMonth === index">
                <q-icon name="check" />
              </q-item-section>
            </q-item>
          </q-list>
        </q-card>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const months = [
      'Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 
      'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'
    ];
    const selectedMonth = ref(new Date().getMonth());

    const selectMonth = (index) => {
      selectedMonth.value = index;
    };

    return {
      months,
      selectedMonth,
      selectMonth,
    };
  },
};
</script>

<style scoped>
.month-list-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.q-list .q-item {
  border-bottom: 1px solid #ccc;
}
.q-list .q-item:last-child {
  border-bottom: none;
}
.q-item-section.side {
  display: flex;
  align-items: center;
}
</style>
