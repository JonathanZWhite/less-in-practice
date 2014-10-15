less-style-guide
================

Style guide for projects that use LESS

##Style

####IDs vs Classes
If a style is used only *once* on the page use an ID otherwise use a class. If you are not sure, go with a class instead of ID. 

####Naming Conventions
Class names should be kept short and use dashes to seperate words. As a rule of thumb, try keep your class numbers under 2 words, 3 max. 

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

##Organization

####Variables
Variables are a great way to maintain consistency across your designs. 

**colors.less**
```
//blues
@light-blue: rgba(111, 203, 250, 1.0);
@medium-blue: rgba(0, 182, 248, 1.0);
@dark-blue: rgba(2, 154, 228, 1.0);

//greys
@light-grey: rgba(226, 226, 226, 1);
@medium-grey: rgba(255, 255, 255, .09);
@dark-grey: rgba(49, 49, 49, 1);
```

####Modularization
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

####Namespacing
Namespace your styles by the module they belong to. In the past, I have tried the prefix your styles by the name of the module they belong to but ended up with unecessarily long class names. The rule with this approach is to keep your nesting within the namespace to a minimum.

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


