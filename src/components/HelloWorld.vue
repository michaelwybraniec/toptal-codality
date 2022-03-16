<template>
  <div>
    <div>
      <h1>BinaryGap</h1>
      <div>
        Write a function that, given a positive integer N, returns the length of
        its longest binary gap. The function should return 0 if N doesn't
        contain a binary gap.
      </div>
      <p>
        Input: <b>{{ decimalList }}</b>
      </p>
      <div>
        <h2>decimalToBinary()</h2>
        <div v-for="(decimal, i) of decimalList" :key="i">
          <b>{{ i }}</b
          >, decimal: <b>{{ decimal }}</b
          >, binary: <b>{{ decimalToBinary(decimal) }}</b
          >, Longest binary gap:
          <b>{{ getLongestBinaryGap(decimalToBinary(decimal)) }}</b>
        </div>
      </div>
      <div>
        <h2>decimalToBinary2()</h2>
        <div v-for="(decimal, i) of decimalList" :key="i">
          <b>{{ i }}</b
          >, decimal: <b>{{ decimal }}</b
          >, binary: <b>{{ decimalToBinary(decimal) }}</b
          >, Longest binary gap:
          <b>{{ getLongestBinaryGap(decimalToBinary2(decimal)) }}</b>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopTal",
  data() {
    return {
      decimalList: [1, 2, 147, 483, 647],
    };
  },
  methods: {
    decimalToBinary(n) {
      const number = n;
      const binary = number.toString(2);
      return binary;
    },
    decimalToBinary2(x) {
      let binary = 0;
      let remainder;
      let i = 1;
      while (x !== 0) {
        remainder = x % 2;
        x = parseInt(x / 2);
        binary = binary + remainder * i;
        i = i * 10;
      }
      return binary.toString();
    },
    getLargestNum(arr) {
      return arr.reduce(function (accumulatedValue, currentValue) {
        return Math.max(accumulatedValue, currentValue);
      });
    },
    getLongestBinaryGap(n) {
      let result = [];
      let gapLength = 0;
      [...n].forEach((n, i) => {
        if (n === "0") gapLength++;
        else {
          if (gapLength > 0) result.push(gapLength);
          gapLength = 0;
        }
      });
      return result.length ? this.getLargestNum(result) : 0;
    },
  },
};
</script>

<style scoped>
</style>
