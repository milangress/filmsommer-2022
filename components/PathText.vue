<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="391.108"
    height="147.962"
    viewBox="0 0 400 160"
  >
    <path
      id="curve"
      d="M.13,113.538s76.3,46.339,169.446,30.993S356.609,67.017,390.886.114"
      transform="translate(0 0)"
      fill="none"
      :stroke="color"
      stroke-width="1"
    />
    <text :fill="color">
      <textPath alignment-baseline="top" xlink:href="#curve">
        {{ text }}
      </textPath>
    </text>
  </svg>
</template>

<script>
export default {
  name: 'PathText',
  props: {
    text: {
      type: String,
      default: 'ERROR',
    },
    color: {
      type: String,
      default: '#000',
    },
  },
}
</script>

<style scoped>
svg {
  position: absolute;
  transform: translateX(-60%);
  /*mix-blend-mode: difference;*/
  z-index: -1;
}
</style>
