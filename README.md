# Cattle Grid

Extremely lightweight, basic flex grid built from a simple sass mixin

## Demo

[Codepen (Grid Only)](https://codepen.io/Ceryni17/pen/dgMYjG)
[Codepen (All)](https://codepen.io/Ceryni17/pen/LgNBXE)


## Getting Started

Cattle grid contains not only a very simple grid (only 6KB minified!) but a small suite of extra settings I've collected over the years of doing Front End. Unlike most frameworks, this grid is easy to isolate and use on it's own - the rest is just for sheer aesthetics and laziness!

To isolate the grid, navigate to **assets/scss/general** and pick **_grid.scss** and add this to your own project

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
$small : (min-width: 0)
$smallOnly : (max-width: 767px)
$medium : (min-width: 768px)
$mediumOnly : (min-width: 767px) and (max-width: 991px)
$large : (min-width: 992px)
$xlarge : (min-width: 1200px)

@mixin breakpoint($small) {
	@content
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


## Authors

* **Ceryni** - *Initial work* - [Ceryni173](https://github.com/Ceryni173)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Inspired by Foundation 6 markup
