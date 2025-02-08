---
title: " GitMath: A Collaborative Math Problem Website "
description: " GitMath is an open-source, community-driven repository of mathematical problems, solutions, and teaching resources.
  It aims to provide a structured database where students can improve their problem-solving skills and teachers can find quality teaching resources.
  The site features problems organized by topic and difficulty, along with hints and solutions to guide students.
  Contributions are welcome to enhance and expand this collaborative platform.
  The site is built using Hugo and hosted on GitLab Pages. "
---



## Quick Search

<div class="search js-only">
  <input type="text" id="search" placeholder="Search ALL Posts...">
  <button id="clear-search">
    <svg xmlns="http://www.w3.org/2000/svg" class="ionicon" viewBox="0 0 512 512"><title>Backspace</title><path d="M135.19 390.14a28.79 28.79 0 0021.68 9.86h246.26A29 29 0 00432 371.13V140.87A29 29 0 00403.13 112H156.87a28.84 28.84 0 00-21.67 9.84v0L46.33 256l88.86 134.11z" fill="none" stroke="currentColor" stroke-linejoin="round" stroke-width="32"></path><path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M336.67 192.33L206.66 322.34M336.67 322.34L206.66 192.33M336.67 192.33L206.66 322.34M336.67 322.34L206.66 192.33"></path></svg>
  </button>
</div>

<script>
// @license magnet:?xt=urn:btih:5ac446d35272cc2e4e85e4325b146d0b7ca8f50c&dn=unlicense.txt Unlicense

document.addEventListener("DOMContentLoaded", () => {
  for (e of document.getElementsByClassName("js-only")) {
    e.classList.remove("js-only");
  }

  const recipes = document.querySelectorAll("#artlist li");
  const search = document.getElementById("search");
  const oldheading = document.getElementById("newest-recipes");
  const clearSearch = document.getElementById("clear-search");
  const artlist = document.getElementById("artlist");

  search.addEventListener("input", () => {
    // grab search input value
    const searchText = search.value.toLowerCase().trim().normalize('NFD').replace(/\p{Diacritic}/gu, "");
    const searchTerms = searchText.split(" ");
    const hasFilter = searchText.length > 0;

    artlist.classList.toggle("list-searched", hasFilter);
    oldheading.classList.toggle("hidden", hasFilter);

    // for each recipe hide all but matched
    recipes.forEach(recipe => {
      const searchString = `${recipe.textContent} ${recipe.dataset.tags}`.toLowerCase().normalize('NFD').replace(/\p{Diacritic}/gu, "");
      const isMatch = searchTerms.every(term => searchString.includes(term));

      recipe.hidden = !isMatch;
      recipe.classList.toggle("matched-recipe", hasFilter && isMatch);
    })
  })

  clearSearch.addEventListener("click", () => {
    search.value = "";
    recipes.forEach(recipe => {
      recipe.hidden = false;
      recipe.classList.remove("matched-recipe");
    })

    artlist.classList.remove("list-searched");
    oldheading.classList.remove("hidden");
  })
})
// @license-end
</script>


## Newest Posts

{{< artlist >}}

## Or Browse by Topic...

{{< tagcloud >}}

## About this site
**GitMath** is a collaborative, open-source platform hosted on GitHub that provides a structured database of mathematical problems, solutions, and teaching resources.

- The platform is built to support **students** who want to practice problem-solving skills and **teachers** who need quality teaching resources.
- Problems are categorized by topic and difficulty, with hints and solutions available to guide students.
- The project is **community-driven**, meaning that anyone can contribute by adding new problems, hints, or solutions.
- This site is maintained using **Hugo**, a fast and flexible static site generator, and is hosted on **GitHub Pages**.
- We welcome contributions and suggestions! If you want to add problems or improve the content, feel free to fork the repository and submit a pull request.

Happy problem-solving! ✨

## Donation

{{< crypto >}}

## All Posts



