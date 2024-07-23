<template>
    <q-layout>
      <q-page-container>
        <q-page class="selection-page">
          <q-card class="q-pa-md">
            <q-list bordered>
              <q-item-label header>Período</q-item-label>
              <q-item v-for="(period, index) in periods" :key="index">
                <q-item-section>
                  <q-radio
                    v-model="selectedPeriod"
                    :val="period.value"
                    :label="period.label"
                  />
                </q-item-section>
              </q-item>
            </q-list>
          </q-card>
  
          <q-card class="q-pa-md q-mt-xl">
            <q-list bordered>
              <q-item-label header>Ano</q-item-label>
              <q-item v-for="year in years" :key="year" clickable @click="selectYear(year)">
                <q-item-section>{{ year }}</q-item-section>
                <q-item-section side v-if="selectedYear === year">
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
      const periods = [
        { label: 'Hoje', value: 'today' },
        { label: 'Essa semana', value: 'thisWeek' },
        { label: 'Esse mês', value: 'thisMonth' },
        { label: 'Esse ano', value: 'thisYear' },
        { label: 'Selecionar', value: 'select' }
      ];
      const years = [2022, 2023, 2024];
      const selectedPeriod = ref(null);
      const selectedYear = ref(2024);
  
      const selectYear = (year) => {
        selectedYear.value = year;
      };
  
      return {
        periods,
        years,
        selectedPeriod,
        selectedYear,
        selectYear,
      };
    },
  };
  </script>
  
  <style scoped>
  .selection-page {
    display: flex;
    flex-direction: column;
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
  