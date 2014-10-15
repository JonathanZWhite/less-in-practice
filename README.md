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

####Modularization
Keep your your LESS modular. For example, instead of having over-sized `main.less`, split your less into files `home.less` or `landing.less` and import them into your `main.less`. 
