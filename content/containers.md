
# Containers

---

## What is a container?
- A "smart" component
- Thin wrappers that connect to the store

---

## What isn't a container?
- The top level component of your feature
- The top level page of your route

---

## Don't think pages - think components

---

## Your component shouldn't care where its data comes from

---

## Containers are meant to keep your components reusable

---

## You can have as many containers as you need

---

## With no extra containers, this tree is tightly coupled

```
| Footer Container <-- Action dispatched here
|-- Footer
|---- Left Panel
|------ Toolbar
|-------- DoSomething Button <-- Event dispatched here
```

---

```
| Footer Container
|-- Footer
|---- Left Panel
|------ Toolbar Container <-- Action dispatched here
|-------- Toolbar <-- Handles layout for children
|----------- DoSomething Button <-- Event dispatched
```

---

## Avoid "Passing Through"
- Your components shouldn't have any inputs/outputs that they don't directly use
- Use content projection and multiple containers to avoid inputs and outputs that are "just passing through"

---

## One container doesn't have to do everything

---

## Containers can handle
- Action dispatching
- Data retrieval
- Decision making about child components

---

## Exercise 4

15 minutes

How can you simplify the following component?

https://stackblitz.com/edit/container-io-refactor-example

---

## My Answer...

