sass-loader
npm install sass-loader sass webpack --save-dev

sass [ssass/scss-filename] [output-filename] if output filename is the same as another file, it overwrites it
use following for autocompile any changes
sass --watch [ssass/scss-filename]:[output-filename] if output filename is the same as another file, it overwrites it

storing colors in a variable:
$main-color: #521751;
also lists:
$border-default: 0.05rem solid $main-color;
Map:
$colors: (main: #521751, secondary: #fa923f);
map.get($colors, main);
Have a color depend on another color automatically:
background: lighten(map.get($colors, main), 72%);
Calculations:
padding: $size-default * 3 0;

partial:
_variables.scss <-- contains all variables
@import "_variables.scss"; <-- imports all variables from the "partial-file"

have a class inherit rules from another class, instead of adding a new class in index.html
@extend .sass-section;

Mixins:
@mixin display-flex () {  <-- save code in a function
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
};

.container {
  @include display-flex(); <-- call the function instead of typing it out again
Passing arguments to Mixins:
  @mixin media-min-width($width) {
  @media (min-width: $width) {
    @content; <-- replaced with body of the function in the function-call
  }
};

html {
  font-size: 94.75%;

  @include media-min-width(40rem) {
    font-size: 125%;  <-- @content replaced with this
  }

&-usage:
  .documentation-link {
    rule;
    rule;

    &:hover,       <--add the hover to the class instead of nested under it
    &:active {     <--add the active to the class instead of nested under it
      rule;
    }
  }