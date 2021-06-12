<template>
  <div>
    <h2>The Next month will start after</h2>
    <br />
    <section class="d-flex flex-row justify-content-center display-2">
      <div>
        {{ d_day }}
      </div>
      <div>
        <span>:</span>
        {{ d_hr }}
      </div>
      <div>
        <span>:</span>
        {{ d_min }}
      </div>
      <div>
        <span>:</span>
        {{ d_sec }}
      </div>
    </section>
  </div>
</template>

<script>
import { render } from "vue";

import Head from "./Header";

export default {
  name: "Count",
  components: {
      Head,
  },
  data: () => ({
    d_day: 0,
    d_hr: 0,
    d_min: 0,
    d_sec: 0,
    d: new Date(),
  }),
  computed: {
    _sec: () => 1000,
    _min() {
      return this._sec * 60;
    },
    _hr() {
      return this._min * 60;
    },
    _day() {
      return this._hr * 24;
    },
  },
  mounted() {
    this.remain();
  },

  methods: {
    remain() {
      const timer = setInterval(() => {
        const now = new Date();
        const end = new Date(2021, 6, 1, 0, 0, 0, 0);
        const dist = end.getTime() - now.getTime();

        if (dist < 0) {
          clearInterval(timer);
          return alert("Next Month has started!!!");
        }

        const day = Math.floor(dist / this._day);
        const hr = Math.floor((dist % this._day) / this._hr);
        const min = Math.floor((dist % this._hr) / this._min);
        const sec = Math.floor((dist % this._min) / this._sec);
        this.d_day = day < 10 ? "0" + day : day;
        this.d_hr = hr < 10 ? "0" + hr : hr;
        this.d_min = min < 10 ? "0" + min : min;
        this.d_sec = sec < 10 ? "0" + sec : sec;
      }, 1000);
    },
  },
};
</script>

<style>
section {
  font-family: helvetica, monospace;
}
</style>



