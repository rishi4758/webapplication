<template>
  <div>
    <form class="form">
      <div class="myButton">
        <i class="fa fa-search" aria-hidden="true"></i>
      </div>
      <input
        class="form-control"
        type="search"
        placeholder="Search"
        aria-label="Search"
        @focus="modal = true"
        v-model="state"
        @input="filterState"
      />
    </form>

    <div v-if="modal === true">
      <ul class="myList" style="width:100%">
        <li
          class="oneValue"
          v-for="suggestion in filterList"
          v-on:click="setModal"
        >
          <NuxtLink
            :to="`/product/${suggestion.id}`"
            class="listValue"
            @click="setModal"
            >{{ suggestion.name }}</NuxtLink
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Data from "../../static/storedata.json";
export default {
  name: "SearchBar",
  data() {
    return {
      list: Data,
      filterList: [],
      modal: false,
      state: "",
    };
  },
  mounted() {
    this.filterState();
  },
  methods: {
    filterState() {
      if (this.state.length === 0) {
        this.filterList = Data;
      } else {
        console.log(this.filterList);
        this.filterList = this.filterList.filter((myState) => {
          return myState.name
            .toLowerCase()
            .startsWith(this.state.toLowerCase());
        });
      }
    },
    setModal() {
      this.modal = false;
    },
  },
};
</script>
<style scoped>
@import "./SearchBar.css";
</style>
