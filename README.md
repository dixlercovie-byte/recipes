# Recipes

A small offline-capable recipes app (PWA). Recipes are stored in your browser (localStorage).

- Add, edit and delete recipes; search; filter by tag or favorites
- Scale servings (numeric ingredient amounts rescale automatically)
- Import / export as JSON, copy ingredients, print
- **Add to shopping list**: sends the (scaled) ingredients to the
  [shopping-list](https://github.com/dixlercovie-byte/shopping-list) app

## Hosting

Static files, no build step. With GitHub Pages (branch `main`, folder `/`) this is served at
`https://<user>.github.io/recipes/`.

The "Add to shopping list" button links to `/shopping-list/index.html`, so it expects the shopping list
to be served from the same domain under `/shopping-list/` (as it is with GitHub Pages for both repos).
Change the path in `sendToShoppingList()` in `index.html` if you host it elsewhere.
