# Component Logic

---

## Selectors vs. Components

---

## Selectors
- Transform data for consumption
- Combine data from different parts of the store
- Derive information from store data

---

## Components
- Simple transformations for visual presentation (e.g. currency)
- Manage simple internal state

---

![No Selectors?](img/noselectors.png)

---

```js
@Input() ticketType: TicketTypeEnum;
get isPremiumTicket(): boolean {
    // Getters will rerun when component updates
	return ticketType === TicketTypeEnum.premium;
}
```

---

## Components can have utilities
No matter how small

---

## Logic files
- Keeps your component files small
- Allows you to write and test pure functions
- Surfaces logic that might be useful in the future for other components

Note: Even if it's never re-used

---

![Label Utility](img/labelutility.png)

---

![Tests](img/labeltests.png)