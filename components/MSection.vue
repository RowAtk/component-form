<template>
  <div class="mb-5">
    <!-- <div class="d-flex ftitle">
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
    </div> -->

    <TextInput :label="'Section'"/>

    <component
      class="p-3 mb-2 border border-primary"
      v-for="(comp, index) in components"
      :key="index"
      :is="components[index]"
    />

    <div class="mt-5">
      <b-dd id="c-dropdown" size="sm" text="Add Component" variant="secondary">
        <div v-for="(comps, type) in componentTypes2" :key="type">
          <b-dd-header>{{ type[0].toUpperCase() + type.slice(1) }}</b-dd-header>
          <b-dropdown-item v-for="(comp, key) in comps" :key="key" @click="addComponent(comp)">{{ key }}</b-dropdown-item>
          <b-dropdown-divider></b-dropdown-divider>
        </div>
      </b-dd>
    </div>
  </div>
</template>

<script>
// import Vue from 'vue'
import TextInput from '~/components/TextInput.vue'
import Doughnut from '~/components/components/Doughnut.vue'

export default {
  components: {
    TextInput,
    Doughnut
  },
  data () {
    return {
      val: '',
      tedit: true,
      componentTypes: {
        charts: ['Doughnut', 'Line', 'Bar'],
        headers: ['Section Header', 'Lvl 1', 'Lvl 2'],
        photos: ['Photo', 'Photo + Caption', 'Collage']
      },
      componentTypes2: {
        charts: {
          Doughnut,
          Line: null,
          Bar: null
        },
        headers: {
          'Section Header': null,
          'Lvl 1': null,
          'Lvl 2': null
        },
        photos: {
          Photo: null,
          'Photo + Caption': null,
          Collage: null
        }
      },
      components: []
    }
  },
  methods: {
    switchModes () {
      if (this.val !== '') {
        this.tedit = !this.tedit
      }
    },
    addComponent (comp) {
      console.log(comp)
      if (comp !== null) {
        this.components.push(comp)
      } else {
        alert('Component does not exist... as yet')
      }
      console.log(this.components)
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
