<template>
  <div>
    <h1>Los mejores JUGADORES DE LA HISTORIA</h1>
    <DataList :dataList="dataList"/>
    <div>
      <input type="text" v-model="newItemText">
      <button @click="añadir">Añadir JUGADOR</button>
    </div>
    <div>
      <button @click="asc">Ordenar Ascendente</button>
      <button @click="desc">Ordenar Descendente</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DataList from './DataList.vue';

interface DataItem {
  text: string;
  backgroundColor: string;
  textColor: string;
}

export default defineComponent({
  components: {
    DataList
  },
  data() {
    return {
      dataList:  [
      { text: 'Lionel Andres MESSI Cuccittini', backgroundColor: 'white', textColor: 'black' },
      ] as DataItem[],
      newItemText: ''
    };
  },
  methods: {
    añadir() {
      if (this.newItemText.trim().length > 0) {
        const newItem: DataItem = {
          text: this.newItemText.trim(),
          backgroundColor: 'white',
          textColor: 'black'
        };
        this.dataList.push(newItem);
        this.newItemText = '';
      }
    },
    asc() {
      this.dataList.sort((a, b) => a.text.localeCompare(b.text));
    },
    desc() {
      this.dataList.sort((a, b) => b.text.localeCompare(a.text));
    }
  }
});
</script>

<style scoped>
.container {
  font-family: Arial, sans-serif;
  text-align: center;
}

h1 {
  margin-bottom: 20px;
  color: #ffffff;
}

button {
  margin: 5px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
input[type="text"] {
  padding: 10px;
  margin-right: 10px;
  border: 5px solid #000000;
  border-radius: 5px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 15px;
  margin-bottom: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
  cursor: pointer;
}

</style>