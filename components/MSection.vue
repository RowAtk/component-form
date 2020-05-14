<template>
  <div class="mb-5">
    <div class="d-flex ftitle">
      Section:
      <div class="ml-2 mr-2 d-flex w-25">
        <input
          id="title"
          v-model="val"
          v-if="tedit"
          value="val"
          type="text"
        >
        <span v-if="!tedit" class="fvalue">  {{ "" + val }}</span>
      </div>
      <div>
        <button v-if="!tedit" @click="switchModes()" class="btn btn-info btn-sm">Edit</button>
        <button v-if="tedit" @click="switchModes()" class="btn btn-info btn-sm">Save</button>
      </div>
    </div>
    <div class="mt-5">
      <b-dd id="c-dropdown" size="sm" text="Add Component" variant="secondary">
        <div v-for="(comps, type) in components" :key="type">
          <b-dd-header>{{ type[0].toUpperCase() + type.slice(1) }}</b-dd-header>
          <b-dropdown-item v-for="(comp, index) in comps" :key="index">{{ comp }}</b-dropdown-item>
          <b-dropdown-divider></b-dropdown-divider>
        </div>
      </b-dd>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      val: '',
      tedit: true,
      components: {
        charts: ['Doughnut', 'Line', 'Bar'],
        headers: ['Section Header', 'Lvl 1', 'Lvl 2'],
        photos: ['Photo', 'Photo + Caption', 'Collage']
      }
    }
  },
  methods: {
    switchModes () {
      this.tedit = !this.tedit
    },
    addSection () {

    },
    getComponents () {

    }
  }
}
</script>

<style scoped>
input {
  height: 100%;
}

button {
  height: 100%;
}

.ftitle {
  color: chocolate;
}

.fvalue {
  color: black;
}
</style>
