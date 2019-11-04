<template>
  <div id="app">
  </div>
</template>

<script>
export default {
};
</script>

<style lang="scss">

  /* - TYPOGRAPHY - */
  /* Custom font - Raleway */
  @import url('https://fonts.googleapis.com/css?family=Raleway:500,600,700&display=swap');

  body {
    -webkit-text-size-adjust:100%; // fix sizing issue on Chrome Mobile
    font-family: "Raleway", sans-serif;
    font-weight: weight(semibold);
  }

  /* Text highlighting */
  ::selection {
    background: color(cold-blue, lighter);
    color: color(plain-white);
  }

  /* Headings h1-h6 and paragraphs p */

  // Incremental font-size
  $min-font-size: 20px;
  $max-font-size: 28px;
  $number-of-sizes: 4; // <h4-6> and <p> share the same value, hence 4 sizes only
  $difference-between-sizes: ($max-font-size - $min-font-size) / $number-of-sizes;

  // <h1>, <h2>, <h3>
  @for $i from 1 through $number-of-sizes {
    $size: $min-font-size + $difference-between-sizes * $number-of-sizes - $i;
    @if $i < 4 {
      h#{$i} {
        @include rfs($size, font-size);
        @include rfs($size + $size * 0.5, line-height);
        @include rfs($size, margin-bottom);
        & +p {
           @include rfs($size * 1.3, margin-bottom);
        }
      }
    }
    // <h4>, <h5>, <h6>, <p>
    @if $i == 4 {
      h4, h5, h6, p {
        @include rfs($size, font-size);
        @include rfs($size + $size * 0.5, line-height);
        @include rfs($size - $size * 0.5, margin-bottom);
      }
      h4, h5, h6, p {
        & +p {
          @include rfs($size * 1.5, margin-bottom);
        }
      }
    }
  }
  /* Links */
  a {
    color: color('cold-blue');
    font-weight: weight(bold);
    text-decoration: none;
    &::selection {
      background: color(cold-blue, light);
      color: color(plain-white);
    }
    &:hover {
      opacity: .8;
    }
  }

</style>
