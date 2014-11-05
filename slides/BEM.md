
###When was the last time you saw (or even wrote) something that looked like this

```sass
.userSelect .userDropdown .user .userLabel {
	// Remember why this is bad?
}
```

---

##Why do we do this?

```sass
.userSelect .userDropdown .user .userLabel {
	// styles...
}
```

- Good:
	- We're in the userSelect
		- This gives us an idea of the context where the style is applied
	- We're styling a user's label
		- this is the what, the important bit.
- Not so good:
	-  Our selector is WAY too specific
		- try overiding one of the styles in here... I dare you
	-  We're basically just mimicking the HTML, but WHY? 
		- What if the structure changes?

---

#This is a bit better

```sass
.userSelect  .userLabel {
	// Still a bit too specific though...
}
```

---
##So let's talk...

---

#BEM

---

#What is BEM?

It is a front-end methodology: a new way of thinking when developing Web interfaces

---

# Block
# Element
# Modifier

---
# Block
## Can exist independently.
---
# Element
## A descendent of a block, doesn't make sense on its own.
---
# Modifier
## Represents a different state or version of a block or element

---

!["Website"](/images/BEM/site.png)

---
##Identify all the independent units 
!["Website"](/images/BEM/site-marked.png)
##These are the _blocks_
---

#Let's zoom in again

---

!["Website"](/images/BEM/head-marked.png)

---

#Enhance...

---

##Identify the blocks and elements
!["Website"](/images/BEM/search-block.png)

---

#Discuss
!["Website"](/images/BEM/search-block-marked.png)

---

#So how do we write represent these concepts in code?

---

#Blocks

```sass
// Block
.achieversForm {
	@include inline-block();
	border: 1px solid $formBorderColor;
	@include border-radius(3px);
	padding 2px 5px;
}

```
---
#Elements
```sass

// Element
.achieversForm-input {
	max-width: 500px;
	border: 1px solid $formFieldBorder;
}
```
---

#Modifiers
```sass
// Modifier

//.achieversForm-disabled,
.achieversForm--disabled {
	background-color: $disabledFormBG;
	border-style: dashed;
}

//.achieversForm-input-error,
.achieversForm-input--error {
	border-color: $errorColor;
	background-color: $errorColorBG;
}
```

