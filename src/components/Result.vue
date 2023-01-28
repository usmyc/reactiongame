<template>
  <div>
    <h1>{{ reaction }}</h1>
    <h2>{{ evaluation }}</h2>
  </div>
</template>

<script>
export default {
  props: ["reaction"],
computed: {
        evaluation() {
        if (this.reaction < 200) {
            return "Fast";
        } else if (this.reaction < 400) {
            return "Normal";
        } else {
            return "Slow";
        }
        },
    },
};
</script>

<style scoped></style>
