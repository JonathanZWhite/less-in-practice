less-in-practice
================

Style guide for projects that use LESS. (Work in progress)

##Style

###IDs vs Classes
For styles that are used only *once* on the page, use an ID, otherwise use a class. If you're not sure, go with a class instead of an ID. Personally, I prefer using classes over IDs in most situations since classes reusable and help keep your code DRY. 

###Naming Conventions
Naming convention can vary from team to team but the general guideline I follow is: keep your class names short and use dashes to separate words. Just as a rule of thumb, I "try" keep my class numbers under 2 words, 3 max. 

```
.editor-tabs {
	height: 135px;
	list-style-type: none;
	margin-left: auto;
	width: 95%;
}

.tile-container {
	margin: 0 auto;
	text-align: center;
	width: 95%;
}
```

###Styles and classes
Keep your classes, within their namespaces, alphabetically organized. Similarly, the styles within the class should also be alphabetic. Organizing in alphabetic order makes your LESS more readable to developers who are looking at your LESS for the first time. Quick tip: Sublime has a built in alphabatizer, simply highlight the styles you want to alphabatize and press control-f5.
```
.webcam-inner {
	border-radius: 50%;
	bottom: 0;
	height: 5px;
	left: 0;
	margin: auto;
	position: absolute;
	right: 0;
	top: 0;
	width: 5px;
}
```

###Spacing 
Separate your classes that share styles out onto different lines. Doing this should help you identify issues or errors in your LESS quickly when given a line number. 
```
.login, 
.logout,
.signup {
	bottom: 0;
	color: rgba(255, 255, 255, 0.7);
	position: absolute;
	right: 45px;
}
```

##Organization

###Variables

####Colors
I prefer RGBA over HEX but which one you use is entirely a matter of preference. Just remember, consistence is key. Bonus: Sublime has a great plugin for converting your colors from HEX to RGBA and back. [CSS Color Converter](https://github.com/TheDutchCoder/ColorConvert) 
```
// Colors (public)
// --------------------------------------------------
@light-blue: rgba(111, 203, 250, 1.0);
@medium-blue: rgba(0, 182, 248, 1.0);
@dark-blue: rgba(2, 154, 228, 1.0);

@light-grey: rgba(226, 226, 226, 1);
@medium-grey: rgba(255, 255, 255, .09);
@dark-grey: rgba(49, 49, 49, 1);
```

####Fonts
Assigning font-sizes semantic meaning is a good way to help you decide what font classes to use and where based on their purpose in your design. 
```
// Font Sizes (private)
// --------------------------------------------------

@display-size: 60px;
@headline-size: 36px;
@title-size: 24px;
@subhead-size: 18px;
@body-size: 16px;
@caption-size: 14px;
```

Unlike font-sizes, I keep my font-weights separate from my font class declarations. That way, you don't have to overwrite the font-weights later on a more case by case basis/ 
```
// Font Weights (public) 
// --------------------------------------------------

@fw-light      200
@fw-normal:    400
@fw-semi-bold: 500
@fw-bold:      700
```

Font classes are where you use your private font-size variables. Don't litter your code with your private variables.  
```
// Font Classes
// --------------------------------------------------

.display {
	font-size: @display-size;
	text-transform: uppercase;
}

.headline {
	font-size: @headline-size;
}
```

####Spacing
Keeping your margin spaces consistent across your designs is key. 
```
// Margin and Spacing (public)
// --------------------------------------------------

@space-jumbo: 100px;
@space-x-large: 50px;
@space-large: 30px;
@space-medium: 25px;
@space-small: 15px;
@space-x-small: 5px;
```

####Z-Index
Instead of using random z-indexes in hopes of achieving the effect you desire, create variables that help you later your design.
```
@z-index-1:   100;
@z-index-2:   200;
@z-index-3:   300;
@z-index-4:   400;
@z-index-5:   500;
@z-index-6:   600;
@z-index-7:   700;
@z-index-8:   800;
@z-index-9:   900;
@z-index-10: 1000;
```

###Global Classes
Keep your code DRY with global classes.
```
// Buttons
// --------------------------------------------------
.btn {
	box-sizing: border-box;
	border-radius: 2px;
	cursor: pointer;
	display: inline-block;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
}

.btn-large {
	height: 45px;
	line-height: 50px;
	padding: 0px 40px;
	vertical-align: middle;
}

// Inputs
// --------------------------------------------------
.input {
	border-radius: 2px;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	box-sizing: border-box;
}

.input-box {
	height: 35px;
	padding: 10px;
	width: 100%;
}
```

###Mixins
LESS is more. Get it? But seriously, mixins are *very* useful but don't abuse them! Instead of using mixins left and right, step back and consider whether it would be better as just a class or as a mixin. 

**Wrong**
```
.btn {
	border-radius: 40px;
	cursor: pointer;
	display: inline-block;
}

.btn-submit {
	.btn;
	font-size: 16px;
	padding: 0px 40px;
}
```

**Better**
```
.btn {
	border-radius: 40px;
	cursor: pointer;
	display: inline-block;
}

.btn-submit {
	font-size: 16px;
	padding: 0px 40px;
}
```

If you are going to use mixins liberally, use parametric mixins to generate dynamic styles.
```
.border-radius(@radius) {
  -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
          border-radius: @radius;
}
```

###Modularization
Keep your your LESS modular. For example, instead of having over-sized `main.less`, split your less into files `home.less` or `landing.less` and import them into your `main.less`. 

```
app/
  |- src/
  |  |- app/
  |  |  |- home
  |  |  |  |- HomeController.js
  |  |  |  |- home.tpl.html  
  |  |  |  |- home.less
  |  |  |- landing
  |  |  |  |- LandingController.js
  |  |  |  |- landing.tpl.html  
  |  |  |  |- landing.less
  |  |- less/
  |  |  |- main.less
```

Especially on large projects with multiple developers, separating out your less files will help prevent conflicts. 
```
// Modules
@import 'colors.less';
@import 'fonts.less';
@import 'mixins.less';
@import 'reset.less';

// Modules
@import '../app/home/home.less';
@import '../app/landing/landing.less';
@import '../app/config/config.less';
@import '../app/dashboard/dashboard.less';
```

###Namespacing
Namespace your styles by the module they belong to. In the past, I have tried the prefix your styles by the name of the module they belong to but ended up with unecessarily long class names. The rule to follow with this approach is to keep your nesting within the namespace to a minimum.

```
.landing {
	.navbar {
		height: 80px;
		list-style-type: none;
		width: 100%;
	}
	
	.navbar-section {
		float: left;
		height: 100%;
		padding: 0px @space-small;
		width: 50%;
	}
	
	background-color: @dark-grey;
	height: 100%;
	overflow: auto;
	text-align: center;
	width: 100%;
}
```


