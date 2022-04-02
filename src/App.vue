<template>
  <div class="main-container" v-on:openModal="changeModalVisibility">
    <div class="search-bar-container">
      <img src="./assets/img/logo.png" alt="logo" class="logo" />
      <div class="search-bar">
        <input
          type="text"
          v-model="searchQuery"
          class="search-bar-input"
          placeholder="Enter Your Favorite Cocktail:"
          @input="callCocktailApi"
        />
        <img
          src="./assets/img/close-icon.svg"
          alt="close icon"
          class="close-icon"
          v-on:click="clearInput"
        />
      </div>
    </div>
    <div class="result-container">
      <ul v-for="(cocktail, index) in cocktailArray" :key="cocktail.key">
        <CocktailResult
          :cocktailName="this.cocktailArray[index].strDrink"
          :cocktailImg="this.cocktailArray[index].strDrinkThumb"
          :cocktailGlass="this.cocktailArray[index].strGlass"
          :cocktailInstructions="this.cocktailArray[index].strInstructions"
          :modalClass="this.modalClass"
          @openModal="changeModalVisibility"
        />
      </ul>
    </div>
    <CocktailModal :modalClass="this.modalClass" @closeModal="hideModal" />
  </div>
</template>

<script>
import CocktailResult from "./components/CocktailResult.vue";
import CocktailModal from "./components/CocktailModal.vue";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      cocktailArray: "",
      searchQuery: "",
      cocktailName: "",
      cocktailImg: "",
      cocktailGlass: "",
      cocktailInstructions: "",

      modalClass: "hidden",
    };
  },
  components: {
    CocktailResult,
    CocktailModal,
  },
  methods: {
    callCocktailApi() {
      axios
        .get(
          `https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${this.searchQuery}
    ` // API Call
        )
        .then((res) => {
          this.cocktailArray = JSON.parse(
            // Only render results if an array is fetched
            JSON.stringify(res.data.drinks || [])
          );
          this.cocktailName = this.cocktailArray[0].strDrink;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    clearInput() {
      this.cocktailArray = "";
      this.searchQuery = "";
    },

    changeModalVisibility() {
      this.modalClass = "";
    },

    hideModal() {
      this.modalClass = "hidden";
    },
  },
};
</script>

<style>
body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  box-sizing: border-box;
  text-align: center;
  background-image: url(../src/assets/img/background.jpg);
  background-size: cover;

  height: 100vh;
  width: 100vw;
  margin: 0;

  display: flex;
  justify-content: center;
  align-items: center;

  color: #f1faee;
}

.main-container {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;

  height: 900px;
  width: 900px;

  padding: 40px;

  background: rgba(0, 0, 0, 0.596);
  border-radius: 20px;
  backdrop-filter: blur(10px);
}

.search-bar-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  width: 100%;
  border-bottom: 2px solid rgba(255, 255, 255, 0.514);
}

.logo {
  display: flex;

  height: 35px;
  margin-bottom: 40px;
}

.search-bar {
  display: flex;
  justify-content: center;
  align-items: center;

  height: 60px;
  width: 600px;

  background: rgba(255, 255, 255, 0.082);

  border-radius: 10px;
  margin-bottom: 40px;

  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

.search-bar-input {
  height: 50px;
  width: 500px;

  text-align: center;
  font-size: 16pt;

  color: white;
  background: transparent;
  border: none;
}

.search-bar-input:focus {
  outline: none;
}

.search-bar-input:focus::placeholder {
  color: transparent;
  font-size: 10pt;
}

.close-icon {
  height: 20px;
}

.close-icon:hover {
  cursor: pointer;
}

.result-container {
  overflow-y: scroll;
  padding-top: 0px;
}
</style>
