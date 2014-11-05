# Object Oriented CSS

> __"<del>Javascript</del> CSS doesn't suck,__
> 
> __you're just doing it wrong."__
>
> Douglas Crockford

---

#Primary concepts of OOCSS

---

## OOCSS concept #1
#Decouple the CSS from the HTML

---

##It may seem to make sense to do this

```sass
.userSelect-Dropdown li {
	//Style list items in the dropdown
}
```

---

#And then along came product...
> __Can you guys create an inline user__
> __select that doesn't use a dropdown?__
>
> Product 

---

#ARRGGGHHH!!!!
#Fucking product!!!!

---

##No
#It's your own damn fault

---

##Change this

```sass
.userSelect-Dropdown li {
	//Style list items in the dropdown
}
```
##To this
```sass
.userSelect-listItem {
	//Style list items ANYWHERE I WANT! :D
}
```
---

## OOCSS concept #2
#Separate Structure From Skin

---
##this looks alright...
```sass
.deleteButton {
	padding: 3px 10px;
	@include border-radius(5px);
	color: $dangerColor;
	border: 1px solid $dangerColor;
	backbround-color: $bgDangerColor;
}

.alertContainer {
	width: 300px;
	font-size: 24px;
	font-weight: bold;
	color: $dangerColor;
	border: 3px dashed $dangerColor;
	backbround-color: $bgDangerColor;
}
```
```
<div class="alertContainer">
	You are about to delete this, are you sure?
</div>

<a href="/delete/item/123" class="deleteButton">Delete</a>
<a href="/home" >cancel</a>

```

---

##But isn't this much nicer?

```sass
.button {
	padding: 3px 10px;
	@include border-radius(5px);
}

.container {
	width: 300px;
	font-size: 24px;
	font-weight: bold;
	border-width: 3px solid;
}

.danger {
	color: $dangerColor;
	border-color: $dangerColor;
	backbround-color: $bgDangerColor;
}
```
```
<div class="container danger">
	You are about to delete this, are you sure?
</div>

<a href="/delete/item/123" class="button danger">Delete</a>
<a href="/home" >cancel</a>
```

---

## OOCSS concept #3
#Separation Of Containers And Content

---
##Meh...
```scss
// Not so hot.
// How can I reuse this to make similar components?
.saleItem {
	float: left;
	width: 25%;
	background-color: $featureBG;
	border: 1px solid $borderColor;
	@include border-radius(3px);
}
```
```
<div class="saleItem">
	...
</div>
<div class="saleItem">
	...
</div>
<div class="saleItem">
	...
</div>
<div class="saleItem">
	...
</div>
```

---

##This looks better!

```
// Ooh, it looks like the .saleItem component can be used anywhere now!

.saleItem {
	background-color: $featureBG;
	border: 1px solid $borderColor;
	@include border-radius(3px);
}

.grid-quarter {
	float: left;
	width: 25%;
}
```
```
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
```

---


##Now lets make a featuredItem!

```
.saleItem {
	background-color: $featureBG;
	border: 1px solid $borderColor;
	@include border-radius(3px);
}

.grid-quarter {
	float: left;
	width: 25%;
}
.grid-half {
	float: left;
	width: 50%;
}
```
```
<div class="grid-half">
	<div class="saleItem">I must be really important</div>
</div>
<div class="grid-half">
	<div class="saleItem">Me too! We are totally bigger</div>
</div>
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
<div class="grid-quarter">
	<div class="saleItem">...</div>
</div>
```

---

#Hold on to your pants...

---

#Introducing: 
#The media object

!["media blocks"](/images/mediaBlocks.png)
---
!["Facbook's media blocks"](/images/Facebook-mediaBlocks.png)
---

---
#How it looks in our platform
```
<div class="mediaObject">

	<div class="mediaObject-leftObj">
	</div>

	<div class="mediaObject-body">
	</div>

</div>
```

---

##Seriously.
#That's it.

```
<div class="mediaObject instaKilogramPost">

	<div class="mediaObject-leftObj">
		<img src="/imgs/chris.jpg" alt="Chris' face">
	</div>

	<div class="mediaObject-body">
		<img src="/pancakes.jpg" alt="pancakes">
		<p>
			Just took a picture of my brunch, cause 
			that's what people do, right?
		</p>
		<div class="comments"> ...more media objects... </div>
	</div>

</div>
```

---


##Nicole Sullivan (@stubbornella), 
##you were right.
#OOCSS is gangster
#as shit.

---

###So please...
#Separate 'dem concerns
##It's worth it later.

---

