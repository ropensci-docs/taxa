# Print that works with color

The same as the `print` function, but can print colored text. Its a bit
of a hack, but the only way I found to replicate the behavior of `print`
without rewriting the entire `print` function.

## Usage

``` r
print_with_color(x, original_length = length(x), ...)
```

## Arguments

- x:

  What to print, typically a character vector

- original_length:

  The length of the full vector if only part was given.

- ...:

  Passed to `print`
