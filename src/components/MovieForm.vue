<template>
  <form @submit.prevent="onSubmit" class="text-center">
    <input
      class="form-control mb-2"
      placeholder="Awesome movie name"
      name="name"
      v-model="name"
      type="text"
    />
    <input
      class="form-control mb-2"
      placeholder="Movie Url"
      name="url"
      v-model="url"
      type="text"
    />
    <input
      class="form-control mb-2"
      placeholder="No of Seasons"
      name="seasons"
      v-model="seasons"
      type="text"
    />
    <select
      class="form-control mb-2"
      name="streaming"
      v-model="streaming"
      id=""
    >
      <option value="" aria-selected="">Streaming services</option>
      <option value="netflix">netflix</option>
      <option value="netflix">Prime</option>
      <option value="netflix">Hulu</option>
    </select>

    <button class="btn btn-info btn-block">Submit</button>
  </form>
</template>


<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "MovieForm",
  props: {
    addMovie: Function,
  },
  data() {
    return {
      name: "",
      url: "",
      seasons: "",
      streaming: "",
    };
  },
  methods: {
    onSubmit: function () {
      this.addMovie({
        name: this.name,
        url: this.url,
        seasons: this.seasons,
        streaming: this.streaming,
        id: uuidv4(),
        date: Date.now(),
      });

      this.name = "";
      this.url = "";
      this.seasons = "";
      this.streaming = "";
    },
  },
};
</script>

<style>
</style>