<script setup>
import { ref } from "vue"

const dice = ref([])

const randomDice = () => {
  const ran = Math.floor(Math.random() * 13)
  dice.value.push(ran)
}

const removeDice = () => {
  const ran = Math.floor(Math.random() * (dice.value.length))
  dice.value.splice(ran, 1)
}

</script>

<template>
  <div>
    <button @click="randomDice">dice</button>
    <button @click="removeDice">remove</button>

    <div class="dices">
      <TransitionGroup name="ela">
        <h1 v-for="d in dice" :key="d" :style="{
          backgroundColor: 'hsl('
            + Math.floor(Math.random() * 360) + ',85%,85%)'
        }">
          {{ d }}
        </h1>
      </TransitionGroup>


    </div>

  </div>
</template>

<style >
body {
  width: 100vw;
  overflow: hidden;
}

.dices {
  display: flex;
  flex-wrap: wrap;
}

h1 {
  padding: 10px;
  margin: 10px;
  text-align: center;
  width: 60px;
}

button {
  padding: 10px 20px;
  margin: 10px 5px;
  text-transform: capitalize;
  font-weight: 800;
}

.ela-enter-from {
  opacity: 1;
  translate: 200px 0;
  rotate: 360deg;
  scale: 0;
}

.ela-enter-to {
  opacity: 1;
  translate: 0px 0;
  rotate: 0deg;
  scale: 1;

}

.ela-enter-active {
  transition: all 0.7s ease-in-out;

}

.ela-leave-active {
  transition: all 0.7s ease-in-out;

}

.ela-leave-from {
  opacity: 1;
}

.ela-leave-to {
  opacity: 0;
  rotate: 360deg;
  scale: 0;
}
</style>