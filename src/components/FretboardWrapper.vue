<script lang="ts" setup>

const stringsCount = 6
const fretsCount = 12
const width = 800
const height = 220
const fretDistance = width / 12

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
              :x1="i*fretDistance"
              :y1="0"
              :x2='i*fretDistance'
              :y2="height"
            />
          </g>
          <!-- Strings (horizontal lines) -->
          <g
            stroke="#222"
            stroke-width="1.5"
          >
            <line
              v-for="i in stringsCount"
              :key="'string-'+i"
              :x1="0"
              :y1="i*10"
              :x2="width"
              :y2="i*10"
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

