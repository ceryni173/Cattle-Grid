# Hunter Grid

Extremely lightweight, basic flex grid built from a simple sass mixin

## Getting Started

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
