<template>
  <div>
    <h1 .display-3>{{ userName }}'s page</h1>
    <h1 .display-2>User id: {{ userNum }}</h1>
  </div>
</template>

<script>
export default {
  asyncData({ params }) {
    return {
      userName: params.username
        .split('-')
        .slice(0, 2)
        .map(item => item.charAt(0).toUpperCase() + item.slice(1))
        .join(' '),
      userNum: parseInt(params.username.match(/[0-9]/g))
    }
  },
  head() {
    return {
      title: `${this.userName}'s page`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: `This is ${this.userName}'s page, the number is ${
            this.userNum
          }`
        }
      ]
    }
  }
}
</script>

<style scoped></style>
