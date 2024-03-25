<template>
  <div>
    <ul v-if="lang === 'Eng'">
      <li v-for="(day, index) in daysEng" :key="index">{{ day }}</li>
    </ul>
    <ul v-else>
      <li v-for="(day, index) in daysRus" :key="index">{{ day }}</li>
    </ul>
    <ul>
      <li v-for="(date, index) in monthDays" :key="index"
       :class="{chosen: date.day === currentDay, disabled: date.day === ''}"
        @click="changeCurrentDay(date)">
        {{ date.day }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    daysEng: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
    daysRus: ['Вос', 'Пон', 'Вт', 'Сре', 'Чет', 'Пят', 'Суб']
  }),
  props: {
    monthDays: {
      type: Number
    },
    currentDay: {
      type: Number
    },
    lang: {
      type: String
    }
  },
  methods: {
    changeCurrentDay(date) {
      if (!date.date == '') {
        this.$emit('changeChosenDay', date.day)
        console.log(date)
      }
    }
  }
}
</script>

<style scoped>
div {
  padding: 10px;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  text-align: center;
}

ul:first-of-type {
  margin-bottom: 10px;
}

ul:last-of-type li {
  padding: 9px;
  cursor: pointer;
  border: 1px solid transparent;
  border-radius: 2px;
}

ul:last-of-type .chosen {
  border: 1px solid rgb(127, 127, 231);
}

ul:last-of-type .disabled {
  cursor: auto;
}
</style>