<template>
  <div class="wrapper">
    <button class="button-lang" type="button" @click="changeLang">{{ lang === 'Eng' ? 'Сhange language' : 'Сменить язык'}}</button>
    <MonthBlock :date="date" @createNewDate="createNewDate" :lang="lang"/>
    <DaysBlock :monthDays="monthDays" :currentDay="currentDay" @changeChosenDay="changeDay" :lang="lang" />
  </div>
</template>

<script>
import DaysBlock from "@/components/DaysBlock.vue"
import MonthBlock from "@/components/MonthBlock.vue"

export default {
  components: {
    DaysBlock,
    MonthBlock
  },
  data: () => ({
    date: new Date(),
    currentDay: new Date().getDate(),
    lang: 'Eng',
  }),
  methods: {
    createNewDate({year, month}) {
      const newDate = new Date(year, month)
      this.date = newDate
    },
    changeDay(day) {
      this.currentDay = day
    },
    changeLang() {
      if(this.lang === 'Eng') {
        this.lang = 'Rus'
      } else {
        this.lang = 'Eng'
      }
    }
  },
  computed: {
    currentYear() {
      return this.date.getFullYear()
    },
    currentMonth() {
      return this.date.getMonth()
    },
    monthDays() {
      const daysArray = []
      const daysCount = new Date(this.currentYear, this.currentMonth + 1, 0).getDate()
      const firstDay = new Date(this.currentYear, this.currentMonth, 1).getDay()
      for(let i = 0; i < firstDay; i++) {
        const dayObject = {
        date: '',
        day: ''
      }
        daysArray.push(dayObject)
      }
      for(let i = 1; i <= daysCount; i++) {
        const dayObject = {
        date: new Date(this.currentYear, this.currentMonth, i),
        day: new Date(this.currentYear, this.currentMonth, i).getDate()
      }
        daysArray.push(dayObject)
      }
      return daysArray
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.wrapper {
  width: 300px;
  min-height: 300px;
  border: 1px solid #b9b9b9;
  border-radius: 2px;
  position: relative;
}

.button-lang {
  position: absolute;
  top: -20px;
  right: 0;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>
