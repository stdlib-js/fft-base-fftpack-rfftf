<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# rfftf

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute the forward discrete Fourier transform (DFT) of a real-valued sequence.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->



<section class="usage">

## Usage

```javascript
import rfftf from 'https://cdn.jsdelivr.net/gh/stdlib-js/fft-base-fftpack-rfftf@esm/index.mjs';
```

#### rfftf( N, r, strideR, offsetR, w, strideW, offsetW )

Computes the forward discrete Fourier transform (DFT) of a real-valued sequence.

```javascript
import Float64Array from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-float64@esm/index.mjs';
import rffti from 'https://cdn.jsdelivr.net/gh/stdlib-js/fft-base-fftpack-rffti@esm/index.mjs';

var N = 4;
var w = new Float64Array( ( 2*N ) + 34 );

rffti( N, w, 1, 0 );

var r = new Float64Array( [ 1.0, 2.0, 3.0, 4.0 ] );

rfftf( N, r, 1, 0, w, 1, 0 );

// r => <Float64Array>[ 10.0, -2.0, 2.0, -2.0 ]
```

The function accepts the following arguments:

-   **N**: length of the sequence to transform. The function is most efficient when this value is a product of small prime numbers.
-   **r**: input array.
-   **strideR**: stride length for `r`.
-   **offsetR**: starting index for `r`.
-   **w**: workspace array containing pre-computed values.
-   **strideW**: stride length for `w`.
-   **offsetW**: starting index for `w`.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   Before calling this function, initialize the workspace by calling [`rffti`][@stdlib/fft/base/fftpack/rffti] with the same sequence length and workspace layout.

-   The function performs the transform in-place (i.e., the input array is **mutated**).

-   For `N = 4`, the output

    ```text
    [ 10.0, -2.0, 2.0, -2.0 ]
    ```

    corresponds to a zero-frequency term `10.0`, a complex coefficient `-2.0 + 2.0i` at frequency `1`, and a Nyquist term `-2.0`.

-   If `N` equals `1`, the function returns early without modifying the input, as a single data point is its own Fourier transform.

-   This transform is unnormalized as a call to this function followed by a call performing a [backward transform][@stdlib/fft/base/fftpack/rfftb] will multiply the input array by `N`.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import zeros from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-zeros@esm/index.mjs';
import discreteUniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-array-discrete-uniform@esm/index.mjs';
import rffti from 'https://cdn.jsdelivr.net/gh/stdlib-js/fft-base-fftpack-rffti@esm/index.mjs';
import rfftf from 'https://cdn.jsdelivr.net/gh/stdlib-js/fft-base-fftpack-rfftf@esm/index.mjs';

var N = 4;
var opts = {
    'dtype': 'float64'
};
var r = discreteUniform( N, -10, 10, opts );
var w = zeros( ( 2*N ) + 34 );

console.log( r );

rffti( N, w, 1, 0 );
rfftf( N, r, 1, 0, w, 1, 0 );

console.log( r );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/fft-base-fftpack-rfftf.svg
[npm-url]: https://npmjs.org/package/@stdlib/fft-base-fftpack-rfftf

[test-image]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/fft-base-fftpack-rfftf/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/fft-base-fftpack-rfftf?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/fft-base-fftpack-rfftf.svg
[dependencies-url]: https://david-dm.org/stdlib-js/fft-base-fftpack-rfftf/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/tree/deno
[deno-readme]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/tree/umd
[umd-readme]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/tree/esm
[esm-readme]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/fft-base-fftpack-rfftf/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/fft-base-fftpack-rfftf/main/LICENSE

[@stdlib/fft/base/fftpack/rffti]: https://github.com/stdlib-js/fft-base-fftpack-rffti/tree/esm

[@stdlib/fft/base/fftpack/rfftb]: https://github.com/stdlib-js/fft-base-fftpack-rfftb/tree/esm

</section>

<!-- /.links -->
