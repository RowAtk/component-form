/* eslint-disable */
<template>
  <div id="form-section">
    <h1>Make Report</h1>
    <hr>
    <div id="rform">
      <!-- <FSection
        v-for="(section, index) in sections"
        :key="index"
      /> -->
      <!-- <h1 v-for="(section, index) in sections" :key="index">{{ section.name }}</h1> -->
      <m-section
        v-for="(section, index) in sections"
        :key="index"
        :name="index"
      />
      <button class="btn btn-light" @click="addSection()">Add Section</button>
    </div>
    <div class="mt-5"><button class="btn btn-info">Generate Form Spec</button></div>
  </div>
</template>

<script>
/* eslint-disable */
import MSection from '~/components/MSection.vue'
export default {
  components: { MSection },
  data () {
    return {
      sections: [],
      currentForm: 0,
      fcomponents: null
    }
  },
  mounted () {
    /*
    const arr = []
    for (let index = 0; index < this.sections.length; index++) {
      const c = () => import('~/components/SForm.vue')
      arr.push(c)
    }
    console.log(arr)
    this.fcomponents = arr
    console.log(this.fcomponents)
    */
  },
  methods: {
    addSection () {
      this.sections.push({ name: 'SECTION' })
    }
  }
}
</script>

<style scoped>
#form-section {
  margin-top: 4rem;
  margin-left: 10rem;
  margin-right: 10rem;
}
</style>
