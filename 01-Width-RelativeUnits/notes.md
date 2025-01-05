# Relative Units

- By Default, HTML document is Responsive
- The developer himself, damages the Responsiveness of the document.
- The 'CSS' is built in such a very that you don't lose any data specified in the HTML document, unless specified explicitly.

---

## Percentages Vs Fixed Width

### width: The Ruler

- Specifies the exact width of an element.
- Can be set using absolute units (e.g., px, cm) or relative units (e.g., %, vw, em).

### Key Traits:

- If content overflows the width, it either gets clipped or triggers scrolling (depending on overflow).
- Fixed and inflexible when set with absolute values.

---

- Absolute units such as `width:800px` restricts the width of the element to 800px at all screen sizes, irrespective of its parent element.
- To avoid this case in our layout, it is always recommended to use values such as `width:80%` to fit the element in all screen sizes.
- Child elements are inherited from parent elements in case of Relative units,
- for example

  ```
  .parent {
    width:80%
  }

  .child {
    with:50%;   // this imples 50% of parent -> 80/2 => 40
  }
  ```

## Percentages on Child

- If we use Absolute units such as 'pixels' for child elements, when the screen sizes become small, these children will overflow the parent elements, which creates a scrollbar horizontally.
- Relative Units such as Percentages depends on its parent element, it constanly changes with respective to its parent element. As a result, it doesn't hinder the Responsiveness.

---

## Why it is a good idea to avoid heights

- Avoiding heights promotes more responsive, user-friendly designs while reducing layout inconsistencies.
- Instead of `height`, using `padding`, `min-height` can provide more adaptable and robust designs.Use heights sparingly and only when necessary.

### Reasons :

1. **Flexibility and Responsiveness:**

   - Specifying a fixed height can make elements rigid, causing layout issues on devices with varying screen sizes. It limits the content's adaptability.

2. **Content Overflow:**

   - Fixed heights often lead to content overflowing or being clipped when the content exceeds the specified height. This can create a poor user experience.

3. **Dynamic Content:**

   - Websites with dynamic or user-generated content benefit from flexible designs, as the height can adapt to fit the content naturally.

---

## Relative Units : em and rem

- `em` and `rem` are relative units, meaning thesome how depends and inherits its values from their parents.
- The parent in this case can be its original parent or html.
- `em` are the units, that depends on the font size specified in its parent Element.
- for example:

```
.parent {
    width:80%;
    font-size:32px;
}

.child {
    width:2em;  // 2 * 32 => 64px
}
```

- If there is no font-size specified in its immediate parent, it checks of its parent's parent elements, this will go up to root html's font size.

- `rem` on the other side, is purely depended on the root html.
- Most browsers set default size as 16px, is referred as 1rem.
- Simply put, `1rem = 16px`

---

## Why you shouldn't set font-sizes using em

- Using `em` for font sizes in CSS can lead to issues primarily due to cascading and compounding effects, which make font size calculations complex and error-prone.

- Two reasons not to use `em` in your font-sizes

1. **Compounding**

- The `em` unit is relative to the font size of the parent element.
- If you nest elements, the font size can grow (or shrink) unexpectedly because each `em` value is calculated based on its parent.

  ```
  body {
  font-size: 16px;
  }
  .container {
  font-size: 1.25em; /_ 16px × 1.25 = 20px _/
  }
  .child {
  font-size: 1.25em; /_ 20px × 1.25 = 25px _/
  }
  ```

2.  **Unpredictable Scaling**
    - When using `em` for font sizes, small changes in one parent element's font size can cascade through its descendants, leading to unintended design changes.
    - Debugging and maintaining such CSS can be challenging.

### When to Use `em`

- Although `em` has drawbacks for font sizes, it’s suitable for:
  1. Padding and margin: To ensure spacing scales proportionally with text size.
  2. Line height: To maintain relative spacing for improved readability.

---

## All about max-width

- The `max-width` property sets the maximum width of an element.
- It ensures the element doesn’t exceed a specified width, even if its content or parent container might suggest otherwise.

### Key Characteristics

1. **Prevents Overflow:**

   - When the content or container is wider than the specified `max-width`, it prevents the element from growing beyond that value.

2. **Responsive Design:**

   - `max-width` works well in fluid/responsive layouts, especially when combined with width or min-width.
   - Using `max-width` with `percentages` or `rem` units ensures adaptability to different screen sizes

3. **Overrides width:**
   - If `width` and `max-width` are both specified, `max-width` takes precedence when the content size exceeds `max-width`.

---

## Relative Units : vh, vw, vmin, vmax

```
Unit	        Definition	                        Example Value (1920x1080 screen)
------------------------------------------------------------------------------------------
vh	        1% of viewport height	                    1vh = 10.8px
vw	        1% of viewport width	                    1vw = 19.2px
vmin	    1% of the smaller viewport dimension	    1vmin = 10.8px
vmax	    1% of the larger viewport dimension	        1vmax = 19.2px
```

---

## A Tale of width and max-width

**Why width Alone Falls Short:**

- Using `width` alone can lead to poor scalability:

```
.content {
  width: 1200px;
}
```

- On a 1920px screen: Looks fine.
- On a 375px mobile screen: Causes horizontal scrolling.

**Why max-width Wins:**

- Adding max-width makes the layout fluid and adaptable:

```
.content {
max-width: 90%;
width: 1200px;
}
```

- On a 1920px screen: Stays within bounds.
- On a 375px screen: Shrinks proportionally.

**Conclusion**

- Use `max-width` for flexibility and responsive layouts.
- Reserve `width` for elements requiring fixed dimensions or predictable behavior.
