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

_I use an autoprefixer on my scss!_



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

---

## Extra mixins & Settings ##

These are just tidbits that come in handy when starting out a new build!


### Sizings ###
```
$small-space: 5px;
$medium-space: 20px;
$large-space: 40px;
$xlarge-space: 60px;
$hundred: ($large-space + $xlarge-space);
$input-height: $large-space;
$border-radius: 3px;
```


### Atom Users!###

If you use Atom - this handy snippet allows for easy autofill of sizes! Be a faster dev

```
'.source.css.scss':
  '5px':
    'prefix': '5px'
    'body': '$small-space';
  '10px':
    'prefix': '10px'
    'body': '($small-space * 2)';
  '15px':
    'prefix': '15px'
    'body': '($small-space * 3)';
  '20px':
    'prefix': '20px'
    'body': '$medium-space';
  '25px':
    'prefix': '25px'
    'body': '($small-space * 5)';
  '30px':
    'prefix': '30px'
    'body': '($xlarge-space / 2)';
  '40px':
    'prefix': '40px'
    'body': '$large-space';
  '50px':
    'prefix': '50px'
    'body': '($small-space * 10)';
  '60px':
    'prefix': '60px'
    'body': '$xlarge-space';
```


### Crayola ###

```
$palette: (
	primary: #8eb8ba,
	primaryText: #fcf8f4,
	secondary: #ebc7ba,
	secondaryText: #697280,
	success: #c9e4bf,
	error: #d38a8a,
	alert: #d38a8a,
	warning: #d29075,
	light-grey: #c4c5c5
);

// shorthand
$primary: map-get($palette, primary);
$primaryText: map-get($palette, primaryText);
$secondary: map-get($palette, secondary);
$secondaryText: map-get($palette, secondaryText);
$light: map-get($palette, light-grey);
```

_To use_

```
background-color: $primary;
color: $primaryText;
```

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

_To use:_

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

_To use:_

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

_To use:_

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

_To use:_

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

_To use:_

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

_To use:_

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

_To use:_

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

_To use:_

```
@include fade(hide)
@include fade(show)
```


---


## Extends ##

### Alignment ###

```
// Columns in a flex grid can be aligned horizontal or vertical inside of their parent.
	.middle-all{
		align-items: center;
		justify-content: center;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.align-middle {
	    align-items: center;
	}

	.align-center {
	    justify-content: center;
	}

// Columns in a flex grid can be aligned horizontal or vertical individually also
	.align-self-bottom {
		align-self: flex-end;
	}

	.align-self-middle {
		align-self: center;
	}

	.align-self-top {
		align-self: flex-start;
	}

// Elements can be absolutely positioned inside of it's relative parent
	.horizontal-center {
		position: absolute;
		left: 50%;
		top: auto;
		transform: translatey(-50%);
	}

	.vertical-center {
		position: absolute;
		left: auto;
		top: 50%;
		transform: translatex(-50%);
	}

	.absolute-center {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}
```

_To use:_

```
@extend .middle-all
@extend .horizontal-center
@extend .vertical-center
@extend .absolute-center

<div class="container">
	<div class="row align-center align-middle">
		<div class="small-12 medium-6 columns align-self-top">column</div>
		<div class="small-12 medium-6 columns align-self-middle column</div>
		<div class="small-12 medium-6 columns align-self-bottom">column</div>
	</div>
</div>
```


### Text Alignment ###

```
// align texts center
.text-center {
	text-align: center;
}
// .. left
.text-left {
	text-align: left;
}
// .. right
.text-right {
	text-align: right;
}
```

_To use:_

```
<div class="container">
	<div class="row align-center align-middle">
		<div class="small-12 large-4 columns text-left">column</div>
		<div class="small-12 large-4 column text-right">column</div>
		<div class="small-12 large-4 columns text-center">column</div>
	</div>
</div>
```

---

## Authors

* **Ceryni** - *Initial work* - [Ceryni173](https://github.com/Ceryni173)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Inspired by Foundation 6 markup
