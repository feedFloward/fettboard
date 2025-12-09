<script lang="ts" setup>

const stringsCount = 6
const fretsCount = 12
const width = 800
const height = 220
const fretDistance = width / (fretsCount - 1)
const stringDistance = height / (stringsCount - 1)

const strings = [
  {"name": "E", "color": "yellow"},
  {"name": "A", "color": "brown"},
  {"name": "D", "color": "brown"},
  {"name": "G", "color": "gray"},
  {"name": "B", "color": "gray"},
  {"name": "e", "color": "lightgray"},
]

const hitMe = function() {
  console.log("hit me!")
}

</script>

<template>
  <v-card class="pa-4" outlined>
    <v-card-title>Fretboard</v-card-title>
    <v-card-text>
      <div class="fretboard-wrapper">
        <svg
          :viewBox="`0 0 ${width} ${height}`"
          preserveAspectRatio="xMidYMidmeet"
        >
          <!-- frets (vertical lines) -->
          <g
            stroke="#333"
            stroke-width="1"
          >
            <line
              v-for="i in fretsCount"
              :key="'fret-'+i"
              :x1="(i - 1)*fretDistance"
              :y1="0"
              :x2='(i - 1)*fretDistance'
              :y2="height"
            />
          </g>
          <!-- Strings (horizontal lines) -->
          <g
            stroke="#222"
            stroke-width="1.5"
          >
            <line
              v-for="_string, i in strings"
              :key="'string-'+_string.name"
              :x1="0"
              :y1="i*stringDistance"
              :x2="width"
              :y2="i*stringDistance"
              :stroke="_string.color"
            />
          </g>
        </svg>
      </div>
    </v-card-text>
  </v-card>
</template>

<style scoped>
  .fretboard-wrapper {
    width: 100%;
    height: 200px;
  }
  svg {
    width: 100%;
    height: 100%;
    display: block;
  }
</style>

