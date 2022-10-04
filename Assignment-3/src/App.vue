<script setup>
import { ref, computed } from "vue";
import data from "./assets/data/data.json";

const search = ref("");
const group = ref("");
const type = ref("");

const filteredData = computed(() => {
  return data.filter((item) => {
    return (
      item.name.toLowerCase().includes(search.value.toLowerCase()) &&
      (group.value === "" || item.group === group.value) &&
      (type.value === "" || item.type === type.value)
    );
  });
});
</script>

<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <input
              type="text"
              class="form-control"
              placeholder="Search by name"
              v-model="search"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <select class="form-control" v-model="group">
              <option value="">Groups</option>
              <option value="IndianRed">IndianRed</option>
              <option value="Orchid">Orchid</option>
              <option value="SteelBlue">SteelBlue</option>
              <option value="YellowGreen">YellowGreen</option>
              <option value="LightSeaGreen">LightSeaGreen</option>
            </select>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <select class="form-control" v-model="type">
              <option value="">All</option>
              <option value="assistant">Assistant</option>
            </select>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <table class="table table-bordered">
            <thead>
              <tr>
                <th>Name</th>
                <th>Group</th>
                <th>Type</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in filteredData" :key="item.id">
                <td>{{ item.name }}</td>
                <td>{{ item.group }}</td>
                <td>{{ item.type }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
