<template>
  <div class="cocktail-modal-container" :class="modalClass">
    <div class="cocktail-modal">
      <div class="div1">
        <div class="transparent-div"></div>
        <h3>{{ cocktailName }}</h3>
        <img
          src="../assets/img/close-icon.svg"
          alt="close icon"
          class="close-icon"
          @click="$emit('closeModal')"
        />
      </div>

      <div class="div2">
        <img src="{modalCocktailImg}" alt="cocktail image" />
      </div>

      <div class="div3">
        <h4>WHICH GLASS?</h4>
        <p>{modalCocktailGlass}</p>

        <h4>DRINK CATEGORY:</h4>
        <p>{modalCocktailType}</p>

        <h4>HOW TO:</h4>
        <p>{modalCocktailDescription}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CocktailModal",
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
.cocktail-modal-container {
  box-sizing: border-box;
  position: fixed;

  height: 50vh;
  width: 50vw;

  display: flex;
  justify-content: center;
  align-items: center;

  background: none;
}
.cocktail-modal {
  height: 410px;
  width: 700px;

  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 0.1fr 0.9fr;
  gap: 0px 0px;
  grid-template-areas:
    "div1 div1"
    "div2 div3";

  padding: 40px;

  background: rgba(0, 0, 0, 0.89);
  border-radius: 20px;
  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px,
    rgba(0, 0, 0, 0.411) 0px -12px 30px, rgba(0, 0, 0, 0.384) 0px 4px 6px,
    rgba(0, 0, 0, 0.404) 0px 12px 13px, rgba(0, 0, 0, 0.295) 0px -3px 5px;
}

.div1 {
  grid-area: div1;

  display: flex;
  justify-content: space-between;
  align-items: center;

  padding-bottom: 40px;
}

h3 {
  font-size: 24pt;
  margin: 0;
  text-shadow: 0 0 3px #f1faeeb9, 0 0 3px #457b92;
}

.close-icon {
  transition: color 0.3s;
  height: 20px;
  box-shadow: none;
}

.close-icon:hover {
  cursor: pointer;
  color: rgba(255, 255, 255, 0.514);
}

.div2 {
  grid-area: div2;
}

img {
  height: 300px;
  border-radius: 10px;
  box-shadow: rgba(80, 80, 80, 0.747) 0px 5px 15px;
}

.div3 {
  margin-left: 30px;
  grid-area: div3;

  overflow-y: scroll;
}

h4 {
  text-align: left;
  margin: 0 0 5px 0;
}

p {
  text-align: left;
  margin: 0 0 20px 0;
}

.hidden {
  display: none;
}
</style>
