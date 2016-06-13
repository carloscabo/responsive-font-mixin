# responsive-font-mixin

This mixin interpolates `font-size` and `line-height` across several mediaquery breakpoints. It fixes a **minimun** font size (in the inferior limit), and a **maximum**. In the animation **below text color changes when entering a new breakpoint**.

<img src="screenshot.gif" alt="Sample image resizing">

# Usage

Define your breakpoints before using the mixin:

````SASS
$small_desktop: 1240px;
$tablet: 1023px;
$mobile: 767px;
$small_mobile: 360px;
````

Include the mixin in the style rules you need it:

````SASS
h1.title {
  margin: 0;
  @include responsive-font (
    (
      // Breakpoint (px), font-size (px), line-height (px)
      // BP must be ordered from big to small
      ( $small_desktop, 64, 72 ),
      ( $tablet,        32, 80 ), // <- Line-height big for testing!
      ( $mobile,        24, 32 ),
      // Down limit to fix minimun size
      // It fixes font-size / line-height to the last value
      ( $small_mobile ) // 360
    ),
    true // debug
  );
}
````

# TO-DO
- Make it unit agnostic (px, ems, %)
