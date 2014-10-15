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

####

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
Namespace your styles by the module they belong to. In the past, I have tried the prefix your styles by the name of the module they belong to but ended up with unecessarily long class names. 

```
.landing {
	background-color: @dark-grey;
	height: 100%;
	overflow: auto;
	text-align: center;
	width: 100%;
}

.navbar {
	height: 80px;
	list-style-type: none;
	width: 100%;
}

.navbar-section {
	float: left;
	height: 100%;
	padding: 0px @space-small 0px @space-small;
	width: 50%;
}

.navbar-text {
	line-height: 80px;
	text-align: right;
}

.navbar-logo {
	color: @smoke-white;
	float: left;
	font-size: 24px;
	font-weight: 400;
	line-height: 80px;
}
```


