<template>
<g>
  <g v-for="marker in all" :key="marker.id">
    <marker v-if="marker.type === 'default'"
      :id="marker.id" orient="auto"
      :markerWidth="15"
      :markerHeight="15"
      :refX="5"
      :refY="5">
      <path d="M 0 5 L 0 5 "
        fill="none" stroke-width="0.8"
        :style="`transform: scale(1);${marker.style}`"/>
    </marker>

    <!-- One (mandatory) -->
    <marker v-if="marker.type === 'one-mandatory-start'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="7.8" refY="5">
      <path d="M 3 5 L 0 5 M 3 2.5 L 3 7.5 M 5 2.5 L 5 7.5 M 5 5 L 7 5"
        fill="none" stroke-width="0.9" stroke="green"
        :style="`transform: scale(1);${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'one-mandatory-end'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="0" refY="5">
      <path d="M 5 5 L 8 5 M 5 2.5 L 5 7.5 M 3 2.5 L 3 7.5 M 3 5 L 1 5"
        fill="none" stroke-width="1" stroke="green"
        :style="`transform: scale(1);${marker.style}`"/>
    </marker>

    <!-- Many (mandatory) -->
    <marker v-if="marker.type === 'many-mandatory-start'"
      :id="marker.id" orient="auto"
      :markerWidth="15"
      :markerHeight="15"
      fill="none" refX="8.3" refY="5"
      >
        <path d="M 0 5 L 5 5 M 5 5 L 0 2.5 M 5 5 L 0 7.5 M 5 2.5 L 5 7.5 M 5 5 L 8 5"
        fill="none" stroke-width="0.8" stroke="green"
        :style="`transform: scale(1);${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'many-mandatory-end'"
      :id="marker.id" orient="auto"
      :markerWidth="15"
      :markerHeight="15"
      fill="none" refX="2.1" refY="5" position="50%"
      >
        <path d="M 10 5 L 5 5 M 5 5 L 10 2.5 M 5 5 L 10 7.5 M 5 2.5 L 5 7.5 M 5 5 L 3 5"
        fill="none" stroke-width="0.8" stroke="green"
        :style="`transform: scale(1);${marker.style}`"/>
    </marker>

    <!-- Zero or One (optional) -->
    <marker v-if="marker.type === 'one-optional-start'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="8" refY="3.2">
      <path d="M 9 8 A 5 5 0 0 1 14 3 A 5 5 0 0 1 19 8 A 5 5 0 0 1 14 13 A 5 5 0 0 1 9 8 Z M 0 8 L 9 8 M 19 8 M 5 3 L 5 13"
        fill="none" stroke-width="2" stroke="green"
        :style="`transform: scale(0.4);${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'one-optional-end'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="0" refY="3.2">
      <path d="M 1 8 A 5 5 0 0 1 6 3 A 5 5 0 0 1 11 8 A 5 5 0 0 1 6 13 A 5 5 0 0 1 1 8 Z L 1 8 M 11 8 L 20 8 M 15 3 L 15 13"
        fill="none" stroke-width="2" stroke="green"
        :style="`transform: scale(0.4);${marker.style}`"/>
    </marker>

    <!-- Zero or Many (optional many) -->
    <marker v-if="marker.type === 'many-optional-start'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="7.6" refY="3.2">
      <path d="M 9 8 A 5 5 0 0 1 14 3 A 5 5 0 0 1 19 8 A 5 5 0 0 1 14 13 A 5 5 0 0 1 9 8 Z M 0 8 L 9 8 M 19 8 M 0 2 L 9 8 L 0 14"
        fill="none" stroke-width="2" stroke="green"
        :style="`transform: scale(0.4);${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'many-optional-end'"
    :id="marker.id" orient="auto"
    :markerWidth="15"
    :markerHeight="15"
    fill="none" refX="0" refY="3.2">
      <path d="M 11 8 A 5 5 0 0 0 6 3 A 5 5 0 0 0 1 8 A 5 5 0 0 0 6 13 A 5 5 0 0 0 11 8 Z M 20 8 L 11 8 M 1 8 M 20 2 L 11 8 L 20 14"
        fill="none" stroke-width="2" stroke="green"
        :style="`transform: scale(0.4);${marker.style}`"/>
    </marker>

    <!-- Defaults -->
    <marker v-if="marker.type === 'arrow-start'"
      :id="marker.id" orient="auto"
      :markerWidth="13 * marker.scale"
      :markerHeight="13 * marker.scale"
      :refX="1 * marker.scale"
      :refY="5 * marker.scale">
        <path d="M0,5 L10,10 L10,0 L0,5"
          :style="`transform: scale(${marker.scale});${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'arrow-end'"
      :id="marker.id" orient="auto"
      :markerWidth="13 * marker.scale"
      :markerHeight="13 * marker.scale"
      :refX="9 * marker.scale"
      :refY="5 * marker.scale">
        <path d="M0,0 L0,10 L10,5 L0,0"
        :style="`${marker.style};transform: scale(${marker.scale})`"/>
    </marker>
    <marker v-if="marker.type === 'square'"
      :id="marker.id" orient="auto"
      :markerWidth="5 * marker.scale"
      :markerHeight="5 * marker.scale"
      :refX="2.5 * marker.scale"
      :refY="2.5 * marker.scale">
        <rect x="0" y="0" width="5" height="5"
          :style="`transform: scale(${marker.scale});${marker.style}`">
        </rect>
    </marker>
    <marker v-if="marker.type === 'circle'"
      :id="marker.id"
      :markerWidth="10 * marker.scale"
      :markerHeight="10 * marker.scale"
      :refX="2.5 * marker.scale"
      :refY="2.5 * marker.scale">
        <circle cx="2.5" cy="2.5" r="2.5"
          :style="`transform: scale(${marker.scale});${marker.style}`">
        </circle>
    </marker>
    <marker v-if="marker.type === 'cross'" :id="marker.id"
      :markerWidth="13 * marker.scale" orient="auto"
      :markerHeight="13 * marker.scale"
      fill="none" refX="5" refY="5" position="50%">
        <path d="M 3,3 L 7,7 M 3,7 L 7,3"
          fill="none" stroke="green" stroke-width="2"
          :style="`transform: scale(${marker.scale});${marker.style}`"/>
      </marker>
      <marker v-if="marker.type === 'arrow-slim-start'"
      :id="marker.id" orient="auto"
      :markerWidth="13 * marker.scale"
      :markerHeight="13 * marker.scale"
      :refX="1 * marker.scale"
      :refY="5 * marker.scale"
      fill="none" stroke="green" stroke-width="2" stroke-linecap="round">
        <path d="M1,5 L9,9 M9,1 L1,5"
          :style="`transform: scale(${marker.scale});${marker.style}`"/>
    </marker>
    <marker v-if="marker.type === 'arrow-slim-end'"
      :id="marker.id" orient="auto"
      :markerWidth="15 * marker.scale"
      :markerHeight="15 * marker.scale"
      :refX="9 * marker.scale"
      :refY="5 * marker.scale" stroke-linecap="round"
      fill="none" stroke="green" stroke-width="2">
        <path d="M10,5 L1,1 M10,5 L1,9"
        :style="`transform: scale(${marker.scale});${marker.style}`"/>
    </marker>
  </g>
</g>
</template>

<script>
/**
 * markers util used to generate and manage markers
 * each default template can be overriden (color, scale, etc)
 * markers component instance is available from Screen component
 */
const defaults = [
// mandatory
{ id: 'one-mandatory-start', type: 'one-mandatory-start', style: 'stroke: #8898aa' },
{ id: 'one-mandatory-end', type: 'one-mandatory-end', style: 'stroke: #8898aa' },
{ id: 'many-mandatory-start', type: 'many-mandatory-start', style: 'stroke: #8898aa' },
{ id: 'many-mandatory-end', type: 'many-mandatory-end', style: 'stroke: #8898aa' },
// optional
{ id: 'one-optional-start', type: 'one-optional-start', style: 'stroke: #8898aa' },
{ id: 'one-optional-end', type: 'one-optional-end', style: 'stroke: #8898aa' },
{ id: 'many-optional-start', type: 'many-optional-start', style: 'stroke: #8898aa' },
{ id: 'many-optional-end', type: 'many-optional-end', style: 'stroke: #8898aa' },

// default
{ id: "default", type: "default", scale: 1, style: "stroke: 8898aa" },
{ id: 'arrow-start', type: 'arrow-start', scale: 0.5, style: 'fill: green' },
{ id: 'arrow-end', type: 'arrow-end', scale: 0.5, style: 'fill: green' },
{ id: 'square', type: 'square', scale: 0.5, style: 'fill: green' },
{ id: 'circle', type: 'circle', scale: 0.5, style: 'fill: green' },
{ id: 'cross', type: 'cross', scale: 1, style: 'fill: none' },
{ id: 'arrow-slim-start', type: 'arrow-slim-start', scale: 0.5, style: 'fill: green' },
{ id: 'arrow-slim-end', type: 'arrow-slim-end', scale: 0.5, style: 'fill: green' }]

export default {
  props: {
    markers: Array //[{ id:String, type:String, scale:Number, style:String }, ...]
  },
  computed: {
    all () {
      return this.markers
        .concat(defaults)
        .map(marker => {
          const base = defaults.find(d => d.type === marker.type)
          if (!base) {
            console.error('unknown marker', marker)
          } else {
            return Object.assign({}, base, marker) // replace marker default attrs
          }
        })
        .filter(marker => marker)
    }
  }
}
</script>