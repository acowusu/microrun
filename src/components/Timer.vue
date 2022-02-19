<template>
  <div class="hello">
    <h2>{{ message }} {{ time }}</h2>
    <div></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    message: String,
  },
  data: () => {
    return {
      last: 0,
      micros: 0,
      cancel: 0,
    };
  },
  created() {
    this.autoUpdate();
  },
  computed: {
    time() {
      try {
        var mins = Math.floor(this.getSeconds / 60);
        var secs = Math.floor((this.getSeconds % 60) / 1000);

        if (mins === 0) {
          return `${secs.toString().padStart(2, "0")}`;
        }
        return `${mins.toString().padStart(2, "0")}:${secs
          .toString()
          .padStart(2, "0")}`;
      } catch {
        console.log("err");
        return 0;
      }
    },
    //       .var quotient = Math.floor(y/x);
    // var remainder = y % x;
    //     }
    getSeconds() {
      return this.micros / 1000;
    },
  },
  methods: {
    autoUpdate() {
      this.micros += performance.now() - this.last;
      this.last = performance.now();
      window.requestAnimationFrame(this.autoUpdate);
    },
    setTime(value) {
      this.micros = value;
    },
    reset() {
      this.setTime(0);
      this.last = performance.now();
    },
  },
};
</script>

<style scoped>
h2 {
  font-size: min(10vw, calc(vh));
  margin: 20px;
}
code {
  font-size: 7vw;
}
button {
  background: #ffffff;
  border: 0;
  padding: 1em;
  border-radius: 50%;
}
</style>