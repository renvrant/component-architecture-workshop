# HTML

---

## JavaScript lets you suck at HTML
(But don't!)

---

## What is good HTML?
- Semantic
- Readable
- Minimal
- Accessible

---

## Why good HTML matters
- Better accessibility
- Better readability
- Smaller page weight
- Easier to spot new components

---

```html
<div (click)="handleClick" class="border">
    <div class="ma4">
        Click <span class="b">here</span>
    </div>
</div>
```

---

## Issues
- A click handler on a div is inaccessible
- More layers of div nesting means more nodes to render
- Can't tell exactly what it represents from looking at it

---

```html
<button (click)="handleClick" class="border pa4">
    Click <strong>here</strong>
</button>
```

---

## Improvements
- Buttons don't require additional development for keypress support
- CSS is condensed - appropriate rules for appropriate place
- Expresses intent to other developers and end users

---

## Accessibility
- Accessibility is a requirement for all apps of a given size
- Using natively interactive elements instead of divs cuts your workload

---

## Without a button
```js
@HostListener('keydown', ['$event'])
  handleKeyDown(event: KeyboardEvent) {
    const code = event.which;
    const isValid = Object.values(this.keyCodes).includes(code);

    if (isValid) {
      event.stopPropagation();
      event.preventDefault();
    }
    
    if (this.keyCodes.space || this.keyCodes.enter) {
      this.handleClick();
    }
  }
```

---

## With a button

```html
<button (click)="handleClick()">
    Click will trigger with keypresses also!
</button>
```

---

## Instead of a div...
- `<button>` - for interactions that won't navigate you away from the page
- `<a>` - for interactions that will navigate you away from the page
- `<ul><li>` - for content that can be expressed as a list (check your for loops!)

---

## Instead of a div...
- `<p>` - for text content
- `<nav>` - for navigational sections
- `<section>` - for components that represent complete sections

Note: Section is useful for component ecosystems. 

---

## When should I use a div?
- Generic division of content
- No keyboard support, or necessary keyboard support doesn't exist
- No better element available

---

## Angular
Take advantage of the host element and ng-container 

---

## The host element
- Defaults to `display: inline` (so set a class)
- Can have classes and attributes assigned to it via the component metadata
- Class lists set through component metadata will be combined with user-added classes

---

```js
@Component({
  selector: 'cw-example-component',
  template: `<ng-content></ng-content>`,
  host: { class: 'block bg-blue pa4' },
})
```

```html
<cw-example-component>
    I will be displayed in a block level element with 
    a blue background and padding
</cw-example-component>
```

---

```html
<cw-example-component class="border">
    I will inherit default styles, but have a border, too!
</cw-example-component>
```

---

```html
<ng-container *ngFor="let item of items">
    <cw-example-component [id]="item.id">
        Iterate multiple things together!
    </cw-example-component>
    <a href="#">{{ item.name }}</a>
</ng-container>
```

---

## React
Don't default to "div" as your bounding element and use React Fragments

---

```html
items.map(item => (
    <React.Fragment>
        <ExampleComponent>
            Iterate multiple things together!
        </ExampleComponent>
        <Link to="#">{item.name}</Link>
    </React.Fragment>
));
```

---

## Exercise 2

10 Minutes

- Refactor the template of the expansion component

https://stackblitz.com/edit/html-refactoring-exercise

---

## My Answer...

https://stackblitz.com/edit/solved-html-refactoring-exercise