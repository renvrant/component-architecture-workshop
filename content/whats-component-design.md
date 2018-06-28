# What is component design?

Note: We will talk about it

---

## Components have several considerations

---

## UI Design
How your components leverage web APIs to present things to the end user

---

## API design
How your components are consumed by other "users"

---

## Interoperability
How your component interacts with the rest of your system, including other components

---

## Components stand alone but exist within a system

---

## What is a well-designed component?
- Encapsulates a single concern
- Loosely coupled and easy to use in many contexts
- Can be used easily; Obscures unnecessary implementation details

---

## What is well-designed component architecture?
- Components can be exchanged quickly and easily
- Components are easy to compose with one another
- Data flow through components is painless

---

## Atomic Design

---

![Atomic Design](img/atomicdesign.png "Atomic Design")

---

> "[ ... ] We can break entire interfaces down into fundamental building blocks and work up from there. That’s the basic gist of atomic design."

---

## Responsibility over size
- Components should have a single responsibility
- In order to achieve this, you will need to have many components of different sizes
---

## When is it a new component?

---

## Did you have to:
- Copy and paste an element or string of tachyons classes?
- Enlarge your window to view the whole template at once?
- Ask yourself "is this a component?"

---

# It's probably a component

---

```html
<p class="error-message block red mt0">
    <img src="alert.svg" alt="">
    Oops! You got an error! 
</p>
```

---

```html
<error-message icon="true">
    Oops! You got an error! 
</error-message>
```

---

## What are the benefits?
- No need to remember which classes belong to the error message
- Enforcing good markup - alt tag for the icon, semantic p tag for the text
- If it changes, it changes in one spot
- If you need to add a new error message, you don't need to think about it
