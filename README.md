![Cattle Grid](http://ceryni.com/cattle-grid/assets/images/logo-type-small.png)

Extremely lightweight, basic flex grid built from a simple mixin

## Demo

[Cattle Grid Example](http://ceryni.com/cattle-grid/)   


## Getting Started

Cattle grid contains not only a very simple grid (only 5KB minified!) but a small suite of extra settings I've collected over the years of doing Front End. Unlike most frameworks, this grid is easy to isolate and use on it's own - the rest is just for sheer aesthetics and laziness!

To isolate the grid, navigate to [grid.scss](https://github.com/ceryni173/Cattle-Grid/blob/master/assets/scss/general/_grid.scss) and add this to your own project! Simple.

If you wish to use the entire project, the folder structure is very simple.

#### General ####
General contains all files needed to set up a new site, from colours, helpers, form elements and mixins

#### Specific ####
Specific contains files related to the project you're about to build.



### Defining Variables

```
$grid-gutter-medium: 30px !default;
$grid-gutter-small: 20px !default;
$global-width: rem-calc(1200px);
$grid-max-width: $global-width + ($grid-gutter-medium * 2) !default;
$grid-columns: 12 !default;

$breakpoint-small: 767px !default;
$breakpoint-medium: 992px !default;
$breakpoint-large: 1200px !default;
$breakpoint-xlarge: 1440px !default;
```

### Using Breakpoint Mixin

```
@mixin breakpoint($media) {
	@media #{$media} {
		@content;
	}
}
```

### Using Grid Markup

```
<div class="container">
	<div class="row">
		<div class="small-12 medium-6 large-3 columns">column</div>
		<div class="small-12 medium-6 large-3 columns">column</div>
		<div class="small-12 medium-6 large-3 columns">column</div>
		<div class="small-12 medium-6 large-3 columns">column</div>
	</div>
</div>
```

## Extra mixins ##

These are just tidbits that come in handy when starting out a new build

### Buttons ###

```
@mixin button-bg($bg, $txt) {
	background: $bg;
	border: $bg;
	color: $txt;
	&:hover,
	&:focus {
		background:darken($bg,10%);
		border:darken($bg, 10%);
		transition: all 0.3s ease;
	}
}
```

To use:

```
@include button-bg(#000000, #ffffff);
```

### Hollow Buttons ###

```
@mixin button-hollow($border, $txt) {
	background: transparent;
	border: 1px solid $border;
	color: $txt;
	&:hover,
	&:focus {
		border: 1px solid darken($border, 10%);
		transition: all 0.3s ease;
		color: darken($txt, 10%);
	}
}
```

To use:

```
@include button-hollow(#000000, #000000);
```

### Pseudos ###

```
@mixin pseudo($display: block, $pos: absolute, $content: ''){
	content: $content;
	display: $display;
	position: $pos;
}
```

To use:

```
@include pseudo;
```

### Placeholders ###

```
@mixin input-placeholder {
	&.placeholder { @content; }
	&:-moz-placeholder { @content; }
	&::-moz-placeholder { @content; }
	&:-ms-input-placeholder { @content; }
	&::-webkit-input-placeholder { @content; }
}
```

To use:

```
@include input-placeholder {
	color: $grey;
}
```

### Headlines ###

```
@mixin heading {
	color: inherit;
	font-weight: 500;
	font-style: normal;
	text-rendering: optimizeLegibility;
	margin-top: 0;
	margin-bottom: 0.5rem;
	line-height: 1.4;
	padding: 0;
}

@mixin h1 {
	@include heading;
	font-size: rem-calc(40);
	@include breakpoint($smallOnly) {
		font-size: rem-calc(30);
	}
}
```

To use:

```
@include h1;
```


### Font sizes ###

```
$body-font-size: 14
@function rem-calc($pixels, $context: $body-font-size) {
	@if (unitless($pixels)) {
		$pixels: $pixels * 1px;
	}
	@if (unitless($context)) {
		$context: $context * 1px;
	}
	@return $pixels / $context * 1em;
}
```

To use:

```
font-size: rem-calc(12)
```


### Z Indexes ###

```
$z-index: (
	modal: 200,
	navigation: 100,
	footer: 10,
	header: 50,
	main: 10,
);

@function z-index($key) {
	@return map-get($z-index, $key);
}
@mixin z-index($key) {
	z-index: z-index($key);
}
```

To use:

```
@include z-index(header);
```

### Fades ###

```
@mixin fade($type) {
	@if $type == 'hide' {
		visibility: hidden;
		opacity: 0;
		transition: visibility 1s, opacity 1s;
	}
	@else if $type == 'show' {
		visibility: visible;
		opacity: 1;
		transition: visibility 1s, opacity 1s;
	}
}
```

To use:

```
@include fade(hide)
@include fade(show)
```


## Authors

* **Ceryni** - *Initial work* - [Ceryni173](https://github.com/Ceryni173)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Inspired by Foundation 6 markup
