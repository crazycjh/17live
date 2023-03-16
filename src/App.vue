<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <div class="" >
    <div class="flex justify-center space-x-2 mt-5">
      <button
        type="button"
        @click="ButtonType1"
        class="inline-block rounded bg-primary px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)]">
        Type 1
      </button>
      <button
        type="button"
        @click="ButtonType2"
        class="inline-block rounded bg-primary px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)]">
        Type 2
      </button>
      <button
        type="button"
        @click="ButtonType3"
        class="inline-block rounded bg-primary px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)]">
        Type 3
      </button>
    </div>
    <list-Component :typedata="typeData"></list-Component>
    <div class="flex justify-center space-x-2 mt-5">
      <button
        type="button"
        @click="ButtonRecipeOne"
        class="inline-block rounded bg-primary px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)]">
        RecipeOne
      </button>
      <button
        type="button"
        @click="ButtonRecipeTwo"
        class="inline-block rounded bg-primary px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_#3b71ca] transition duration-150 ease-in-out hover:bg-primary-600 hover:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:bg-primary-600 focus:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)] focus:outline-none focus:ring-0 active:bg-primary-700 active:shadow-[0_8px_9px_-4px_rgba(59,113,202,0.3),0_4px_18px_0_rgba(59,113,202,0.2)]">
        RecipeTwo
      </button>
    </div>
    <dish-Recipe :recipes="recipeInput"></dish-Recipe>
  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

import listComponent from './components/listComponent.vue';
import dishRecipe from './components/dishRecipe.vue'
import { ref } from "vue";
export default {
  
  name: 'App',
  components: {
    // HelloWorld,
    listComponent,
    dishRecipe
  },
  setup(){
    //list 
    const type1 = [{name:"Anna",year:10,class:"A"},{name:"Mark",year:10,class:"M"}]
    const type2 = [{title:"Javascript Info",category:"book",rating:10},{title:"Fantasy",category:"movie",rating:5}]
    const type3 = [{winner:"Amy",rank:1},{winner:"Bob",rank:2},{winner:"jack",rank:2}]
    
    const typeData = ref([]);

    const ButtonType1 = ()=>{
      typeData.value = type1;
     
    }
    const ButtonType2 = ()=>{
      typeData.value= type2;
    }
    const ButtonType3 = ()=>{
      typeData.value = type3;
    }

    //recipe
    const recipeInput= ref([]);
    const recipeOne = [   ["Salad", "Tomato", "Cucumber", "Salad", "Sauce"],
                          ["Pizza", "Tomato", "Sausage", "Sauce", "Dough"],
                          ["Quesadilla", "Chicken", "Cheese", "Sauce"],
                          ["Sandwich", "Salad", "Bread", "Tomato", "Cheese"]];
    const recipeTwo = [ ["Pasta", "Tomato Sauce", "Onions", "Garlic"],
                        ["Chicken Curry", "Chicken", "Curry Sauce"],
                        ["Fried Rice", "Rice", "Onions", "Nuts"],
                        ["Salad", "Spinach", "Nuts"],
                        ["Sandwich", "Cheese", "Bread"],
                        ["Quesadilla", "Chicken", "Cheese"]];

    const ButtonRecipeOne = ()=>{
      recipeInput.value = recipeOne;
    }
    const ButtonRecipeTwo = ()=>{
      recipeInput.value = recipeTwo;
    }
    return {ButtonType1,ButtonType2,ButtonType3,typeData,recipeInput,ButtonRecipeOne,ButtonRecipeTwo}
  }
}
</script>

<style>

</style>
