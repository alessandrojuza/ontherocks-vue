<template>
  <div class="cocktail-result" @click="$emit('openModal')">
    <img :src="cocktailImg" alt="cocktail-image" />
    <p>{{ cocktailName }}</p>
    <div class="explore-button">
      <img
        src="../assets/img/arrow-forward-icon.svg"
        alt="arrow icon"
        class="arrow-icon"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "CocktailResult",
  props: {
    cocktailName: {
      type: String,
    },
    cocktailImg: {
      type: String,
    },
    cocktailGlass: {
      type: String,
    },
    cocktailInstructions: {
      type: String,
    },
    modalClass: {
      type: String,
    },
  },
};
</script>

<style scoped>
.cocktail-result {
  box-sizing: border-box;
  display: flex;
  justify-content: space-between;
  align-items: center;

  height: 120px;
  width: 800px;

  margin: 20px 0 20px 0;
  padding: 20px;

  background: rgba(255, 255, 255, 0.082);
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;

  transition: background 0.3s, box-shadow 0.3s;
}

.cocktail-result:hover {
  background: rgba(255, 255, 255, 0.151);
  cursor: pointer;
  box-shadow: rgba(0, 0, 0, 0.719) 0px 5px 15px;
}

img {
  height: 80px;
  border-radius: 5px;
}

p {
  font-size: 14pt;
  font-weight: 600;
}

.explore-button {
  display: flex;
  justify-content: center;
  align-items: center;
}

.arrow-icon {
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(288deg)
    brightness(102%) contrast(102%);

  height: 15px;
}

@media screen and (max-width: 991px) {
  .cocktail-result {
    width: 580px;
  }
}

@media screen and (max-width: 600px) {
  .cocktail-result {
    width: 460px;
  }
}

@media screen and (max-width: 480px) {
  .cocktail-result {
    width: 320px;
  }

  p {
    font-size: 12pt;
    padding: 0 5px 0 5px;
  }
}
</style>
