<template>
  <div>
    <p class="text-primary font-weight-bold font-italic">Doughnut Chart</p>
    <text-input :label="'Title'"/>
    <div
      class="d-flex mb-3"
      v-for="index in dataCount"
      :key="index"
    >
      <text-input :label="'x'" :number="true" />
      <text-input :label="'y'" :number="true" />
    </div>
    <button class="btn btn-light" @click="addDataField()">Add Data Item</button>
    <!-- size selection -->
    <div class="mt-3">
      Size (Circumference)
      <select class="form-control w-auto" name="size" id="size" >
        <option>Full</option>
        <option>Half</option>
      </select>
    </div>
  </div>
</template>

<script>
import TextInput from '~/components/TextInput.vue'
export default {
  name: 'Doughnut',
  components: {
    TextInput
  },
  data () {
    return {
      data: [],
      dataCount: 0
    }
  },
  methods: {
    addDataField () {
      this.dataCount = this.dataCount + 1
    }
  },
  render (createElement) {
    return createElement('div',
      `<text-input :label="'Title'"/>
      <div
        class="d-flex mb-3"
        v-for="index in dataCount"
        :key="index"
      >
        <text-input :label="'x'" :number="true" />
        <text-input :label="'y'" :number="true" />
      </div>
      <button class="btn btn-light" @click="addDataField()">Add Data Item</button>
      <!-- size selection -->
      <div class="mt-3">
        Size (Circumference)
        <select class="form-control w-auto" name="size" id="size" >
          <option>Full</option>
          <option>Half</option>
        </select>
      </div>`
    )
  }
}
</script>

<style scoped>

</style>
