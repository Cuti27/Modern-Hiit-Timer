<template>
  <div class="hiit">
    <label for="timer">{{ this.tempHeating }}</label>
    <div class="timer">
      <div class="inside-timer">
        <number-label
          size="M"
          upper
          :value="actualMin"
          label="Minutos"
        ></number-label>
        <number-label
          size="M"
          upper
          :value="actualSeg"
          label="Segundos"
        ></number-label>
      </div>

      <div>
        <button>Reiniciar</button>
        <button @click="startInterval()">Comenzar</button>
      </div>
    </div>
  </div>
</template>

<script>
import NumberLabel from "@/components/NumberLabel";
export default {
  components: {
    NumberLabel,
  },
  data: function () {
    return {
      tempHeating: this.heating,
      tempStretch: this.stretch,
      tempHigh: this.high * this.repetitions,
      tempLower: this.lower * this.repetitions,
      actualHigh: true,
    };
  },
  mounted: function () {},
  computed: {
    actualMin() {
      if (this.tempHeating > 0) {
        return Math.floor((this.tempHeating / 60) % 60);
      } else if (this.actualHight && this.tempHigh > 0) {
        return Math.floor((this.tempHigh / this.high / 60) % 60);
      } else if (!this.actualHight && this.tempLower > 0) {
        return Math.floor((this.tempLower / this.lower / 60) % 60);
      } else if (this.tempStretch) {
        return Math.floor((this.tempStretch / 60) % 60);
      } else {
        return 0;
      }
    },
    actualSeg() {
      if (this.tempHeating > 0) {
        return this.tempHeating - this.actualMin * 60;
      } else if (this.actualHight && this.tempHigh > 0) {
        return this.tempHigh - this.actualMin * 60;
      } else if (!this.actualHight && this.tempLower > 0) {
        return this.tempLower - this.actualMin * 60;
      } else if (this.tempStretch) {
        return this.tempStretch - this.actualMin * 60;
      } else {
        return 0;
      }
    },
  },
  methods: {
    startInterval: function () {
      setInterval(() => {
        this.startTimer();
        console.log("[DEBUG]");
      }, 1000);
    },
    startTimer: function () {
      if (this.tempHeating > 0) {
        this.tempHeating--;
      } else if (this.actualHight && this.tempHigh > 0) {
        this.tempHigh--;
      } else if (!this.actualHight && this.tempLower > 0) {
        this.tempLower--;
      } else if (this.tempStretch) {
        this.tempStretch--;
      }
    },
  },
  props: {
    repetitions: {
      type: Number,
      default: 15,
    },
    heating: {
      type: Number,
      default: 180,
    },
    stretch: {
      type: Number,
      default: 180,
    },
    high: {
      type: Number,
      default: 120,
    },
    lower: {
      type: Number,
      default: 90,
    },
  },
};
</script>

<style lang="scss" scoped>
.timer {
  display: flex;
  justify-content: center;
  flex-direction: row;
  inside-timer {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
}
</style>