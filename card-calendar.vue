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
   const months = [
     'Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 
     'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'
   ];
   const selectedMonth = ref(new Date().getMonth());

   const selectMonth = (index) => {
     selectedMonth.value = index;
   };
  //parte 2
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
     months,
     selectedMonth,
     selectMonth,
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
.month-list-page {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  height: 100%;
  gap: 80px; 
}
.q-list .q-item {
 border-bottom: 1px solid #ccc;
 color: #1A3B47;
 font-family: "Roboto";
}
.q-list .q-item:last-child {
 border-bottom: none;
 color: #1A3B47;
 font-family: "Roboto";
}
.q-item-section.side {
 display: flex;
 align-items: center;
}
/* parte 2 */
/* .selection-page {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
  } */
  .q-list .q-item {
    border-bottom: 1px solid #ccc;
    color: #1A3B47;
    font-family: "Roboto";
  }
  .q-list .q-item:last-child {
    border-bottom: none;
  }
  .q-item-section.side {
    display: flex;
    align-items: center;
  }
</style>
