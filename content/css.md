# CSS

---

## CSS vs. Components

---

## Many of your atomic components are probably CSS styles

---

## Why a component over a CSS class?
- Consistency
- Discoverability
- Maintainability

---

## Why CSS over a component?
- Lower cost of implementation
- Higher tolerance of variance
- Greater flexibility

Note: greater flexibility is a pro and a con

---

## Greater flexibility is not always a good thing

---

## Prefer components

Note: They highlight problems in your project much faster than CSS

---

## Functional CSS vs. Component-Scoped CSS

---

## Functional CSS (Tachyons)
- "Componentized" and modular
- Enforces consistency
- Performance improvements

---

## Component-Scoped CSS
- Fully encapsulated
- Enables more complex CSS techniques

---

## Both is good

Note: Porque no los dos?!

---

## Global CSS
Should be reserved for truly global utilities and constants

---

## What makes for good global constants?
- Colours
- Spacing
- Project-specific, annotated z-index scale
- Animation information

---

# Context-specific styling

---

## Layout components
- Compose other components
- Should only be responsible for styling that composition

---

## Components with style variations
Each component should be responsible for its own style variants

---

```css 
/* Good for a layout component! */
.child-component + .child-component {
    padding-left: 2rem;
}

/* Bad for a layout component! */
:host >>> .child-component {
    background: blue;
}
```

---

## Angular
- You can style the `:host` element explicitly and in conjunction with other selectors
- `:host-context` lets you style a component specific to certain contexts 

---

```css
:host-context(cw-parent-component) {
  background: blue;
}
:host(.active) {
  color: red;
}
```

---

## React with Styled Components
- You can use components as selectors to style components within a given context

---
```js
const Child = styled.nav`
  color: red;
  
  ${ParentComponent} & {
    background: blue;
  }
```