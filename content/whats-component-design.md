# What is component design?

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

## But how do I break my components down?

---

## Responsibility over size
- Components should have a single responsibility
- In order to achieve this, you will need to have many components of different sizes
---

## When is it a new component?

---

## Did you have to:
- Copy and paste an element or string of tachyons classes?
- Add a new edge case for an existing component?
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

---

## Exercise 1

2 Minutes

Start building a rating component. It needs to:
- Show an image and title of what is being rated
- Accept a rating value to display
- Allow the user to click on a star to rate the item

---

![Rating Component](img/starratingcomponent.png "Rating Component")

---

## Part 2:

3 Minutes

Discuss:
- Where did you start your planning?
- How did you approach breaking the component down?
- What worked? What didn't?

---


![Rating Component](img/starratingbreakdown.png "Rating Component")

---

## Think about how it's used and work backwards

---

```html
<star-rating [rating]="3.5">
  <star-button (click)="handleRating(1)"></star-button>
  <star-button (click)="handleRating(2)"></star-button>
  <star-button (click)="handleRating(3)"></star-button>
  <star-button (click)="handleRating(4)"></star-button>
  <star-button (click)="handleRating(5)"></star-button>
</star-rating>
```

---

```html
<star-rating [rating]="3.5" [max]="5" (onRate)="handleRating($event)">
</star-rating>
```

---

```html
<star-button *ngFor="let starNumber of max"
             [value]="getStarValue(starNumber)"
             (click)="onRate.emit(starNumber)"
             class="pr1 dib"
>
  {{ starNumber }}
</star-button>
```
