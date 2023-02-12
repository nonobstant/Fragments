<template>
    <div class="grid grid-cols-7 gap-1 w-80 mx-auto mt-6">
      <div v-for='(_case, index) in board' :key="index" class="w-10 h-10">
        <div v-if="isPair(index)" class="bg-slate-800 dark:bg-purple-300 w-full h-full"></div>
        <div v-else class="bg-slate-200 dark:bg-purple-700 w-full h-full"></div>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      board : []
    }
  },
  methods : {
    isPair(num) {
      if (num%2 == 0) {
        return true
      } else {
        return false
      }
    }
  },
  mounted() {
    for (let index = 0; index < 49; index++) {
      var _case = {
        num : index
      }
      this.board.push(_case)
    }
  }
}
</script>

<style>
</style>
