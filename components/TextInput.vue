<template>
  <div class="mb-2 mr-4">
    <div class="d-flex ftitle">
      {{ label }}:
      <div class="ml-2 mr-2 d-flex w-auto">
        <input
          v-model="val"
          v-if="tedit"
          type="text"
        >
        <span v-if="!tedit" class="fvalue">  {{ "" + val }}</span>
      </div>
      <div>
        <button v-if="!tedit" @click="switchModes()" class="btn btn-info btn-sm">Edit</button>
        <button v-if="tedit" @click="saveVal()" class="btn btn-info btn-sm">Save</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    value: [String, Number],
    number: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      tedit: true,
      val: null
    }
  },
  mounted () {
    this.val = this.value == null ? '' : toString(this.value)
  },
  methods: {
    switchModes () {
      console.log(this.val)
      if (this.val !== '' && this.val) {
        this.tedit = !this.tedit
      }
    },
    saveVal () {
      if (this.number) {
        const v = parseFloat(this.val)
        if (!isNaN(v)) {
          this.val = v
          this.switchModes()
        } else {
          alert('Value must be numeric')
        }
      } else {
        this.switchModes()
      }
    }
  }
}
</script>

<style scoped>
.ftitle {
  color: chocolate;
}

.fvalue {
  color: black;
}
</style>
