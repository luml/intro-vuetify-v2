<template>
  <v-container>
    <h1>Dashboard</h1>
    <v-row>
      <v-col cols="12" v-for="item in sales" :key="item.label" md="3">
        <v-card
          v-ripple
          elevation="9"
          tile
          class="shopping-item"
          color="primary"
        >
          <v-icon>{{ item.icon }}</v-icon>
          <v-img src="https://picsum.photos/510/300?random" aspect-ratio="1.7" contain>
            <v-card-title>{{ item.label }}</v-card-title>
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
        </v-card>
      </v-col>
    </v-row>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
    ></v-data-table>
    <v-row v-if="loadNewContent" v-intersect="showMoreContent">
      <v-col cols="6" sm="4">
        <v-img
          src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"
          gradient="to top right, rgba(100,115,201,.33), rgba(25,32,72,.7)"
        ></v-img>
      </v-col>

      <v-col cols="6" sm="4">
        <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg">
          <div class="fill-height bottom-gradient"></div>
        </v-img>
      </v-col>

      <v-col cols="6" sm="4">
        <v-img src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg">
          <div class="fill-height repeating-gradient"></div>
        </v-img>
      </v-col>
    </v-row>
    <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
      You have selectd {{ currentItem }}
      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">Close</v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      loadNewContent: true,
      sales: [
        {
          label: "Bags",
          icon: "mdi-bag-personal-outline",
        },
        {
          label: "Shoes",
          icon: "mdi-shoe-heel",
        },
        {
          label: "Hats",
          icon: "mdi-account-cowboy-hat",
        },
        {
          label: "Gloves",
          icon: "mdi-boxing-glove",
        },
      ],
      currentItem: "",
      snackbar: false,
      text: `Hello, I'm a snackbar`,
      headers: [
        {
          text: "Dessert (100g serving)",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Calories", value: "calories" },
        { text: "Fat (g)", value: "fat" },
        { text: "Carbs (g)", value: "carbs" },
        { text: "Protein (g)", value: "protein" },
        { text: "Iron (%)", value: "iron" },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: "1%",
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: "1%",
        },
        {
          name: "Eclair",
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: "7%",
        },
        {
          name: "Cupcake",
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: "8%",
        },
        {
          name: "Gingerbread",
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: "16%",
        },
        {
          name: "Jelly bean",
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: "0%",
        },
        {
          name: "Lollipop",
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: "2%",
        },
        {
          name: "Honeycomb",
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: "45%",
        },
        {
          name: "Donut",
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: "22%",
        },
        {
          name: "KitKat",
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: "6%",
        },
      ],
    };
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.currentItem = event.name;
    },
    showMoreContent(entries) {
      // More information about these options
      // is located here: https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API
      // this.loadNewContent = entries[0].isIntersecting;
      console.log(entries)
    },
  },
};
</script>

<style scoped>
.shopping-item {
  height: auto;
  margin: 2px;
}
.bottom-gradient {
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0.4) 0%, transparent 72px);
}

.repeating-gradient {
  background-image: repeating-linear-gradient(
    -45deg,
    rgba(255, 0, 0, 0.25),
    rgba(255, 0, 0, 0.25) 5px,
    rgba(0, 0, 255, 0.25) 5px,
    rgba(0, 0, 255, 0.25) 10px
  );
}
</style>
