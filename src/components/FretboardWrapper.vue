<script lang="ts" setup>

const stringsCount = 6
const fretsCount = 12
const width = 800
const height = 220
const fretDistance = width / (fretsCount - 1)
const stringDistance = height / (stringsCount - 1)

const strings = [
  {"name": "E", "color": "yellow", "notes": {0: "E", 1: "F", 2: "F#", 3: "G", 4: "G#", 5: "A", 6: "A#", 7: "B", 8: "C", 9: "C#", 10: "D", 11: "D#", 12: "E"}},
  {"name": "A", "color": "brown", "notes": {0: "A", 1: "A#", 2: "B", 3: "C", 4: "C#", 5: "D", 6: "D#", 7: "E", 8: "F", 9: "F#", 10: "G", 11: "G#", 12: "A"}},
  {"name": "D", "color": "brown", "notes": {0: "D", 1: "D#", 2: "E", 3: "F", 4: "F#", 5: "G", 6: "G#", 7: "A", 8: "A#", 9: "B", 10: "C", 11: "C#", 12: "D"}},
  {"name": "G", "color": "gray", "notes": {0: "G", 1: "G#", 2: "A", 3: "A#", 4: "B", 5: "C", 6: "C#", 7: "D", 8: "D#", 9: "E", 10: "F", 11: "F#", 12: "G"}},
  {"name": "B", "color": "gray", "notes": {0: "B", 1: "C", 2: "C#", 3: "D", 4: "D#", 5: "E", 6: "F", 7: "F#", 8: "G", 9: "G#", 10: "A", 11: "A#", 12: "B"}},
  {"name": "e", "color": "lightgray", "notes": {0: "E", 1: "F", 2: "F#", 3: "G", 4: "G#", 5: "A", 6: "A#", 7: "B", 8: "C", 9: "C#", 10: "D", 11: "D#", 12: "E"}},
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
            <g
              v-for="_string, i in strings"
              :key="'string-'+_string.name"
            >
              <!-- whole string lines -->
              <line
                :x1="0"
                :y1="i*stringDistance"
                :x2="width"
                :y2="i*stringDistance"
                :stroke="_string.color"
              />
              <!-- single notes -->
              <line
                v-for="fret, note in Object.entries(_string.notes)"
                :key="'stringPart-'+_string.name+fret+note"
                :x1="parseInt(fret) * fretDistance"
                :y1="i*stringDistance"
                :x2="(parseInt(fret) + 1) * fretDistance"
                :y2="i*stringDistance"
              />
            </g>
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

