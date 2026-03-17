<template>
  <div class="appShell">
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base="currentBase"
      :creamer="currentCreamer"
      :syrup="currentSyrup"
    />

    <ul class="controls">
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`temp-${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>

      <li>
        <template v-for="base in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="base"
              :id="`base-${base.id}`"
              :value="base"
              v-model="currentBase"
            />
            {{ base.name }}
          </label>
        </template>
      </li>

      <li>
        <template v-for="syrup in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`syrup-${syrup.id}`"
              :value="syrup"
              v-model="currentSyrup"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>

      <li>
        <template v-for="creamer in creamers" :key="creamer.id">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`creamer-${creamer.id}`"
              :value="creamer"
              v-model="currentCreamer"
            />
            {{ creamer.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import {
  temps,
  bases,
  syrups,
  creamers,
  currentTemp,
  currentBase,
  currentSyrup,
  currentCreamer,
} from "./stores/beverage";
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

.appShell {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
}

.controls {
  list-style: none;
  padding: 0;
  margin: 0;
}

.controls li {
  margin-bottom: 0.6rem;
}

.controls label {
  margin-right: 0.75rem;
  color: black;
}
</style>