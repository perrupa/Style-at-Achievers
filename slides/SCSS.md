#SASS @ Achievers

---
#Variables
```
$achieversColor: #bada55;

.awesomeTitle {
	color: $achieversColor;
}
```
---
#Naming
### Name your variables by what they _represent_
### Not by what they _contain_


``` sass
$achieversBlue: #A0A;
/* Hey Guys, remember when we rebranded? Why is achieversBlue = purple? */

$primeColor: #00A;
/* Thank god we actually used this name! */
```
---

#Nesting

``` sass
.selector {
	width: auto;
	.nest {
		color: #bada55;

		&.awesome {
			font-weight: bold;
		}
	}
}
```

becomes

``` sass
.selector {
	width: auto;
}
	.selector .nest {
		color: #bada55;
	}
	.selector .nest.awesome {
		font-weight: bold;
	}
```

---

#But this can be *VERY* bad

- Specificity wars are wars
	- and war is bad

---

# Don't start wars.

---

# The Inception rule

### "Never go more than 3 levels deep"

---

#Extending Classes

``` sass
.island {
 -webkit-border-radius: 3px;
	 -moz-border-radius: 3px;
	  -ms-border-radius: 3px;
	   -o-border-radius: 3px;
		  border-radius: 3px;
	padding: 10px;
	border: 1px solid #F2F2F2;
}

.errorBox {
	/* take all the styles from island*/
	@extend .island;

	/* Add our own*/
	background-color: #FDD;
	border-color: red;
}

```

---

#Mixins
``` sass
@mixin border-radius($radius: 3px) {
	/* Cross-browser sexiness */
  -webkit-border-radius: $radius;
	 -moz-border-radius: $radius;
	  -ms-border-radius: $radius;
	   -o-border-radius: $radius;
		  border-radius: $radius;
}

.island {
	@include border-radius();
	padding: 10px;
	border: 1px solid #F2F2F2;
}

.squareIsland {
	@extend .island;
	@include border-radius(0px);
}
```

---

#Placeholders
```
%roundedContainer {
	border-radius 3px;
	padding: 10px;
}

.island {
	@extend %roundedContainer;
	color: seashell;
	background-color: sandybrown;
}
```

generates

```
/* Note there is no roundedContainer selector output */
.island {
	border-radius: 3px;
	padding: 10px;
}

.island {
	color: seashell;
	background-color: sandybrown;
}
```


---

## Mixins vs Extending Classes

```sass
@mixin mTest() {
	color: red;
	width: 300px;
}

%pTest {
	color: blue;
	width: 300px;
}
```

Let's try it out

---

```sass
.caseOne {
	@include mTest();
}

.caseTwo {
	@include mTest();
}
```

generates

```sass
.caseOne {
	color: red;
	width: 300px;
}

.caseTwo {
	color: red;
	width: 300px;
}
```

---
#Extending Classes

```sass
.caseOne {
	@extend %pTest;
}

.caseTwo {
	@extend %pTest;
}
```

generates

```sass
.caseOne,
.caseTwo {
	color: red;
	width: 300px;
}
/* Damn, that's nice */
```

---

#Compass Mixins

Compass is a library of mixins for sass

---

##Some handy mixins we commonly use include:

much more at [www.compass-style.org](www.compass-style.org)

```sass
//Cross browser includes, one line - all browsers :)
@include inline-block( middle );
@include border-radius( 3px );
@include box-shadow( $shadowColor 0 1px 0 0 inset );
@include text-shadow( 0 1px 0 $shadowColor );
@include background-image( linear-gradient(top, $gradColStart, $gradColEnd) );
```

---

##Abuse File Imports

```sass
// Our global_stylesheet.scss
@import "compass";
@import "jquery-ui/jquery-ui-achievers-theme";
@import "icons";
@import "base";
@import "global_deprecated";
```

---

#File Structure

```
- desktop
	- components
		We need more in here.
	- ie 
		hopefully this a thing of the past ".ie7 &"
	- features
		We need less in here.
	- fonts
	- platform_components
	- variables
- mobile
	- thar be dragons...

```

---

#Why the shit are there so many underscores?
#What is this, PHP?

---

#Partials

A partial is a file that is not meant to stand on its own. They are prepended with an underscore which indicates that it will not be compiled unless it is included.

You don't need to include the underscore in the path when importing it into, SASS can figure that out.
