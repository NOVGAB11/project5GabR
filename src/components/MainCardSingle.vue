<script setup>
    import { faker } from '@faker-js/faker'
    const recipeTitle = faker.lorem.words(4); 
    const prepTime = faker.datatype.number() + ' minutes'; 
    const cookTime = faker.datatype.number() + ' minutes'; 
    const servingSize = faker.datatype.number(); 

     const ingredients = Array.from({ length: 7 }, () => {
         return faker.datatype.number() + 'g ' + faker.food.ingredient();
     });

    const instructions = Array.from({ length: 6 }, () => faker.lorem.sentence());

    const firstname = faker.person.firstName();
    const lastname = faker.person.lastName();
    const username = faker.internet.userName({ firstName: firstname, lastName: lastname }).toLowerCase();
    const bio = faker.lorem.lines(2);

    const foodImage = faker.image.food();
</script>

<template>
    <div>
    <h1 class="text-2xl font-bold text-center text-green-600">{{ recipeTitle }}</h1>
    <img class="object-fill h-40 w-90 rounded-xl shadow-lg" v-bind:src="faker.image.urlLoremFlickr({category: 'food', height: 45, width: 96})" />

    <p class="text-lg font-medium text-green-600">>Prep Time: <span class="font-normal text-green-500">{{ prepTime }}</span></p>
    <p class="text-lg font-medium text-green-600">Cooking Time: <span class="font-normal text-green-500">{{ cookTime }}</span></p>
    <p class="text-lg font-medium text-green-600">Number of Servings: <span class="font-normal text-green-500"> {{ servings }}</span></p>

    <h2 class="text-2xl font-bold text-center text-green-600">Your Ingredients</h2>
    <ul>
      <li v-for="ingredient in ingredients" :key="ingredient">{{ ingredient }}</li>
    </ul>

    <h2 class="text-2xl font-bold text-center text-green-600">Cooking Instructions : </h2>
    <ol>
      <li v-for="(step, index) in instructions" :key="index">{{ step }}</li>
    </ol>

    <p class="text-lg font-medium text-green-800">This recipe was created by: {{ firstname }} {{ lastname }}</p>
    <p class="text-lg font-medium text-green-800">Username: {{ username }}</p>
    <p class="text-lg font-medium text-green-800">Bio: {{ bio }}</p>
  </div>
</template>