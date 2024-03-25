<template>
  <div>
    <button type="button" @click="this.$emit('createNewDate', {
      month: date.getMonth() - 1,
      year: date.getFullYear()
    })">
      <svg fill="#000000" width="20" height="20" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><path d="m4.431 12.822 13 9A1 1 0 0 0 19 21V3a1 1 0 0 0-1.569-.823l-13 9a1.003 1.003 0 0 0 0 1.645z"></path></g></svg>
    </button>
    <span v-if="lang === 'Eng'">{{ `${monthsEng[date.getMonth()]} ${date.getFullYear()}` }}</span>
    <span v-else>{{ `${monthsRus[date.getMonth()]} ${date.getFullYear()}` }}</span>
    <button type="button" @click="this.$emit('createNewDate', {
      month: date.getMonth() +  1,
      year: date.getFullYear()
    })">
      <svg fill="#000000" width="20" height="20" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><path d="m4.431 12.822 13 9A1 1 0 0 0 19 21V3a1 1 0 0 0-1.569-.823l-13 9a1.003 1.003 0 0 0 0 1.645z"></path></g></svg>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    date: {
      type: String
    },
    lang: {
      type: String
    }
  },
  data: () => ({
    monthsEng: {
      0: 'Jan',
      1: 'Feb',
      2: 'Mar',
      3: 'Apr',
      4: 'May',
      5: 'Jun',
      6: 'Jul',
      7: 'Aug',
      8: 'Sep',
      9: 'Oct',
      10: 'Nov',
      11: 'Dec'
    },
    monthsRus: {
      0: 'Янв',
      1: 'Фев',
      2: 'Мар',
      3: 'Апр',
      4: 'Май',
      5: 'Июн',
      6: 'Июл',
      7: 'Авг',
      8: 'Сен',
      9: 'Окт',
      10: 'Ноя',
      11: 'Дек'
    }
  })
}
</script>

<style scoped>
div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
}

button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}

button:last-of-type {
  transform: rotateY(180deg);
}
</style>