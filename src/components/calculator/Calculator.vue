<script setup>
import {ref} from "vue";

const inputNumber = ref("")
const operator = ref("")

const result = ref(0)
const isShowResult = ref(true)
const resultStyle = ref("result")

function input(e) {
  if (isShowResult.value) {
    isShowResult.value = false
  }

  inputNumber.value += e.target.innerText
  console.log(`inputNumber.value: ${inputNumber.value}`)
}

function calculate(e) {
  if (operator.value === "") {
    result.value = Number(inputNumber.value)
    operator.value = e.target.innerText
    showResult()
    return;
  }

  let number = Number(inputNumber.value)
  console.log(`계산 - ${result.value} ${operator.value} ${number}`)

  if (operator.value === '+')
    result.value += number
  if (operator.value === '-')
    result.value -= number
  if (operator.value === 'x')
    result.value *= number
  if (operator.value === '/')
    result.value /= number

  console.log(`계산결과 - ${result.value}`)

  operator.value = e.target.innerText
  showResult()
}

function equals(e) {
  e.target.value = ""
  calculate(e)
  showResult()
}

function initialize() {
  result.value = 0
  showResult()

  console.log(`inputNumber.value: ${inputNumber.value}\nresult.value: ${result.value}`)
}

function showResult() {
  isShowResult.value = true
  inputNumber.value = ""
}
</script>

<template>
  <h1>계산기</h1>
  <div>
    <table>
      <tbody>
      <tr>
        <td colspan="4" :class="resultStyle">
          <p v-if="isShowResult">{{ result }}</p>
          <p v-else>{{ inputNumber }}</p>
        </td>
      </tr>
      <tr>
        <td @click="initialize" colspan="3">
          AC
        </td>
        <td @click="calculate">/</td>
      </tr>
      <tr>
        <td @click="input">7</td>
        <td @click="input">8</td>
        <td @click="input">9</td>
        <td @click="calculate">x</td>
      </tr>
      <tr>
        <td @click="input">4</td>
        <td @click="input">5</td>
        <td @click="input">6</td>
        <td @click="calculate">-</td>
      </tr>
      <tr>
        <td @click="input">1</td>
        <td @click="input">2</td>
        <td @click="input">3</td>
        <td @click="calculate">+</td>
      </tr>
      <tr>
        <td colspan="2" @click="input">0</td>
        <td>.</td>
        <td @click="equals">=</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
  table {
    border-collapse: collapse;
  }

  td {
    padding: 5px 10px;
    text-align: center;
    border-color: black;
  }

  .result {
    color: whitesmoke;
    text-align: right;
  }
</style>
