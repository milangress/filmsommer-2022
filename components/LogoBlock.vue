<template lang="pug">
.logos
  div(v-for="logo in logos")
    //object.sponsor-logo(
    //  type="image/svg+xml"
    //  :data="`logos/${logo.file}`"
    //  )
    img.sponsor(
      :src="`logos/${logo.file}.svg`"
      loading="lazy"
      alt="Sponsor Logo"
    )
</template>

<script>
export default {
  name: 'LogoBlock',
  data() {
    return {
      logos: [],
    }
  },
  fetch() {
    // const dataDates = await fetch(
    //   process.env.baseUrl +
    //     'files?filter[folder][_eq]=dd889dad-a9de-4c9b-b8cd-f67ab74cb6d5'
    // ).then((response) => response.json())
    // this.logos = await dataDates.data
    // // eslint-disable-next-line no-console
    // console.log(this.logos)
    this.logos = Array.from(Array(23).keys()).map((i) => ({
      file: `sponsor_logo_${i}`,
    }))
  },
  methods: {
    getImage(fileId) {
      const url = new URL(`${process.env.baseUrl}assets/${fileId}`)
      return url.href
    },
  },
}
</script>

<style scoped>
.logos {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-auto-rows: auto;
  grid-gap: 2rem;
  background-color: white;
  padding: 2rem;
}
@media (max-width: 1100px) {
  .logos {
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}
@media (max-width: 800px) {
  .logos {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
