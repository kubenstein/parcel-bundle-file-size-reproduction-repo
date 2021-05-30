<template>
  <div class="helloWorld">
    <h1>Hello {{ who }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      who: "loading...",
    };
  },

  mounted() {
    setTimeout(() => {
      this.who = "Parcel";
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.helloWorld {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
