# Input & Output

---

## Your component's Input/Output are it's API
So think like an API designer!

---

## What makes an API painful?

---

## Good API design
- Consistent
- Minimal
- Intuitive
- Easy to use

---

## Consumers shouldn't have to...
- Know how your component works internally
- Reformat data for your component to use it
- Keep track of too many inputs

---

## Keep it Simple
Components should require only the minimum amount of data they need to function

---

```js
@Component({
  template: 
  `<ng-container *ngIf="!data.loading">
     <cw-img [url]="cat.picUrl" [id]="cat.id"></cw-img>
     {{ caption }}
  </ng-container>`
})
class BadCatPic {
    @Input() data: {
      loading: boolean,
      cat: {
        picUrl: string,
        id: number,
      },
    };
    @Input() caption: string;
}
```

---

```js
@Component({
  template:
  `<ng-container *ngIf="!loading">
     <cw-img [url]="picUrl" [id]="id"></cw-img>
     <ng-content></ng-content>
  </ng-container>`
})
class GoodCatPic {
    @Input() cat: {
      picUrl: string,
      id: number,
    };
    
    get loading(): boolean {
      return !Boolean(this.person);
    }
}
```

---

```html
<best-cat-pic *ngIf="cat" [cat]="cat">
    My cat is very cool and important
</best-cat-pic>
```

---

## Props vs. Content Projection

---

## Props/Inputs are good for
- Typed data
- Data that is not directly renderable
- Data that will be transformed or processed

---

## Content Projection/Children
- Arbitrary text or other content
- Content that may take many different forms
- Elements that the component is only responsible for formatting

---

## Multi-content projection

Note: Components can be used exclusively for formatting and encapsulating styles

---

```html
<jb-dialog-title [hideCloseButton]="hideCloseButton">
  <ng-content select="[jbDialogTitle]"></ng-content>
</jb-dialog-title>

<jb-dialog-content>
  <ng-content></ng-content>
</jb-dialog-content>

<jb-dialog-actions>
  <ng-content select="[jbDialogActions]"></ng-content>
</jb-dialog-actions>
```

---

```html
<!-- Login dialog -->
<jb-dialog>
  <ng-container jbDialogTitle>Sign in</ng-container>
  <jb-login></jb-login>
  <ng-container jbDialogActions>
    <button (click)="close()">Cancel</button>
    <button (click)="login()">Login</button>
  </ng-container>
</jb-dialog>

```