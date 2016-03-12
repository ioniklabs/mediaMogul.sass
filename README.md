## mediaMogul.sass

### About: 
a simple sass library for managing media queries in responsive design
 
### How To Use:

``` scss 
/**
 * include mediaMogul.[sass/scss]
 */
@import 'mediaMogul.*';

/**
 * @param $definition    ['ss', '>ss', 'xs', '>xs', '<sm', '<=sm', 'sm', '>=sm', '>sm', '<md', '<=md', 'md', '>=md', '>md', '<lg', 'lg', '<xl', 'xl']
 * @param $mediatype     mediatype e.g. 'screen', 'print', 'all'
 */
@include mq($definition, [$mediatype: 'only screen']) {
 ...
}
```
### example:

``` scss 
@import 'mediaMogul.scss';

.wrapper {
  width: 100%;
  @include mq('>=sm') {
    margin-left: auto;
    margin-right: auto;
  }
  @include mq('sm') {
    max-width: 640px;
  }
  @include mq('>=md') {
    max-width: 960px;
  }
}
```
would compile to
``` css 
.wrapper {
  width: 100%;
}
@media only screen and (min-width: 768px) {
  .wrapper {
    margin-left: auto;
    margin-right: auto;
  }
}
@media only screen and (min-width: 768px) and (max-width: 991px) {
  .wrapper {
    max-width: 640px;
  }
}
@media only screen and (min-width: 992px) {
  .wrapper {
    max-width: 960px;
  }
}
```
### settings
breakpoint definitions follow the same format as Bootstrap allowing for out of the box integration. If you would like to mediaMogul with another framework or custom breakpoints the below variables should be set before mediaMogul is included in the project. *support for custom definitions is in the pipeline*
``` scss
$screen-xs:       480px !default;
$screen-sm:       768px !default;
$screen-md:       992px !default;
$screen-lg:       1200px !default;
$screen-xl:       1920px !default;
```
