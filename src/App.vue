<template>
  <div class="main-container">
    <div class="search-bar-container">
      <img src="./assets/img/logo.png" alt="logo" class="logo" />
      <div class="search-bar">
        <input
          type="text"
          value=""
          class="search-bar-input"
          placeholder="Enter Your Favorite Cocktail:"
        />
        <CloseIcon class="close-icon" onClick="{}" />
      </div>
    </div>
  </div>

  <div className="result-container"></div>
</template>

<script>
// import CocktailResult from "./components/CocktailResult.vue";

export default {
  name: "App",
  components: {
    CocktailResult,
  },
};
</script>

<style>
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
  border-bottom: 2px solid $transparent-white;
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
  transition: color 0.5s;
}

.close-icon:hover {
  cursor: pointer;
  color: $transparent-white;
}

.result-container {
  overflow-y: scroll;
  padding-top: 0px;
}
</style>
