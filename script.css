const searchBtn = document.getElementById("search-btn");
const searchInput = document.getElementById("search-input");
const recipeList = document.getElementById("recipe-list");
const recipeModal = document.getElementById("recipe-modal");
const recipeDetails = document.getElementById("recipe-details");
const closeBtn = document.getElementById("close-btn");

searchBtn.addEventListener("click", () => {
  const query = searchInput.value.trim();
  if (query) {
    fetchRecipes(query);
  }
});

function fetchRecipes(query) {
  fetch(`https://www.themealdb.com/api/json/v1/1/search.php?s=${query}`)
    .then(res => res.json())
    .then(data => {
      displayRecipes(data.meals);
    })
    .catch(err => {
      console.error("Fetch error", err);
      recipeList.innerHTML = `<p style="color:red;">Something went wrong!</p>`;
    });
}

function displayRecipes(meals) {
  recipeList.innerHTML = "";

  if (!meals) {
    recipeList.innerHTML = "<p>No recipes found.</p>";
    return;
  }

  meals.forEach(meal => {
    const card = document.createElement("div");
    card.className = "recipe-card";
    card.innerHTML = `
      <img src="${meal.strMealThumb}" alt="${meal.strMeal}">
      <h3>${meal.strMeal}</h3>
    `;
    card.addEventListener("click", () => showDetails(meal));
    recipeList.appendChild(card);
  });
}

function showDetails(meal) {
  let ingredients = "";
  for (let i = 1; i <= 20; i++) {
    const ingredient = meal[`strIngredient${i}`];
    const measure = meal[`strMeasure${i}`];
    if (ingredient && ingredient.trim()) {
      ingredients += `<li>${measure} ${ingredient}</li>`;
    }
  }

  recipeDetails.innerHTML = `
    <h2>${meal.strMeal}</h2>
    <img src="${meal.strMealThumb}" alt="${meal.strMeal}">
    <p><strong>Category:</strong> ${meal.strCategory}</p>
    <p><strong>Area:</strong> ${meal.strArea}</p>
    <h3>Ingredients:</h3>
    <ul>${ingredients}</ul>
    <h3>Instructions:</h3>
    <p>${meal.strInstructions}</p>
  `;

  recipeModal.classList.remove("hidden");
}

closeBtn.addEventListener("click", () => {
  recipeModal.classList.add("hidden");
});
