<template>
  <div class="q-pa-md q-gutter-y-xs column items-stretch">
    <div id="calculated" class="items-end">
      <h3 class="col-shrink">{{ state.current }}</h3>
    </div>
    <q-btn-group>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="clearCalculator"
        label="C"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="changeSign"
        label="+/-"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="percentage"
        label="%"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="divide"
        label="/"
      ></q-btn>
    </q-btn-group>
    <q-btn-group>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('7')"
        label="7"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('8')"
        label="8"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('9')"
        label="9"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="multiply"
        label="X"
      ></q-btn>
    </q-btn-group>
    <q-btn-group>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('4')"
        label="4"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('5')"
        label="5"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('6')"
        label="6"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="subtract"
        label="-"
      ></q-btn>
    </q-btn-group>
    <q-btn-group>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('1')"
        label="1"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('2')"
        label="2"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('3')"
        label="3"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="sum"
        label="+"
      ></q-btn>
    </q-btn-group>
    <q-btn-group>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('0')"
        label="0"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="appendNumber('00')"
        label="00"
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="numberColor"
        :ripple="{ center: true }"
        @click="decimal"
        label="."
      ></q-btn>
      <q-btn
        square
        :size="size"
        :color="utilityColor"
        :ripple="{ center: true }"
        @click="equal"
        label="="
      ></q-btn>
    </q-btn-group>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'CalculatorComponent',

  setup() {
    const state = reactive({
      previous: '',
      current: '',
      operator: '',
      operatorClicked: false,
    });
    const numberColor = 'accent';
    const utilityColor = 'warning';
    const size = 'lg';

    function clearCalculator() {
      state.current = '0';
    }

    function changeSign() {
      state.current =
        state.current.charAt(0) === '-'
          ? state.current.slice(1)
          : `-${state.current}`;
    }

    function percentage() {
      state.current = `${parseFloat(state.current) / 100}`;
    }

    function appendNumber(number: string) {
      if (state.operatorClicked) {
        state.current = '';
        state.operatorClicked = false;
      }
      state.current = `${state.current}${number}`;
    }

    function decimal() {
      if (state.current.indexOf('.') === -1) {
        state.current = `${state.current}.`;
      }
    }

    function setPrevious() {
      state.previous = state.current;
      state.operatorClicked = true;
    }

    function divide() {
      // state.operator = (a: number, b: number) => a / b;
      state.operator = '/';
      setPrevious();
    }

    function multiply() {
      // state.operator = (a: number, b: number) => a * b;
      state.operator = '*';
      setPrevious();
    }

    function subtract() {
      // state.operator = (a: number, b: number) => a - b;
      state.operator = '-';
      setPrevious();
    }

    function sum() {
      // state.operator = (a: number, b: number) => a + b;
      state.operator = '+';
      setPrevious();
    }

    function equal() {
      state.current = eval(
        `${parseFloat(state.previous)}${state.operator}${parseFloat(
          state.current
        )}`
      );
      state.previous = '';
    }

    return {
      state,
      numberColor,
      utilityColor,
      size,
      clearCalculator,
      changeSign,
      percentage,
      appendNumber,
      decimal,
      divide,
      multiply,
      subtract,
      sum,
      equal,
    };
  },
});
</script>
