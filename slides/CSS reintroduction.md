#CSS Re-introduction

---

#Display Types

---

#Block

- Take up the entire row
- width:auto
	- very different from 100%
---

#Inline
- No Width
	- expands horizontally to accomodate its content and then wraps.
- white space between elements shows
- Cannot be given height, width, padding, margin, etc...
	- Content is king

---

# Inline-block
- A block element box that will be flowed with surrounding content as if it were a single inline box

---

# Positioning

---

# Static

- Static positioning is the default and should be used whenever possible.
- The staticly positioned element will behave as you would normally expect based on its display type.
- Technically, it is "no positioning"

---

# Relative

- Similar to static, but I can be positioned `relative` to my original position using top, left, right and/or bottom
	- The space a relative object occupies is where it would be positioned staticly
	- But it does not take occupy any space where it is rendered

---

# Absolute

- Absolutely positioned elements are displayed :
	- "relative" to
		- the nearest parent container
			- that is positioned (meaning: not static)

---

# Floats

- When an element is floated it is taken out of the normal "flow" of the document
	- shifted to the left or right of its parent container
- Because they are outside of the flow of the document:
	- An element containing only floats will have no height
	- This is why...

---

# Clear Them!

- use the `cf` class
- PLEASE do not use `<div class="clear"></div>`
	- it is hard to keep track of

---

# Centering and Aligning

- Try and use inline-block and inline elements where possible
- Then you can use  `text-align:(left|right|center);`
