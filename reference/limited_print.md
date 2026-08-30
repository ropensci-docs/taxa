# Print a subset of a character vector

Prints the start and end values for a character vector. The number of
values printed depend on the width of the screen by default.

## Usage

``` r
limited_print(
  chars,
  prefix = "",
  sep = ", ",
  mid = " ... ",
  trunc_char = "[truncated]",
  max_chars = getOption("width") - nchar(prefix) - 5,
  type = "message"
)
```

## Arguments

- chars:

  (`character`) What to print.

- prefix:

  (`character` of length 1) What to print before `chars`, on the same
  line.

- sep:

  What to put between consecutive values

- mid:

  What is used to indicate omitted values

- trunc_char:

  What is appended onto truncated values

- max_chars:

  (`numeric` of length 1) The maximum number of characters to print.

- type:

  (`"error"`, `"warning"`, `"message"`, `"cat"`, `"print"`, `"silent"`,
  `"plain"`)

## Value

`NULL`

## Examples

``` r
taxa:::limited_print(1:100)
#>  1, 2, 3, 4, 5, 6, 7, 8, 9 ... 92, 93, 94, 95, 96, 97, 98, 99, 100
taxa:::limited_print(1:10000)
#>  1, 2, 3, 4, 5, 6, 7 ... 9994, 9995, 9996, 9997, 9998, 9999, 10000
taxa:::limited_print(1:10000, prefix = "stuff:")
#> stuff: 1, 2, 3, 4, 5, 6, 7 ... 9995, 9996, 9997, 9998, 9999, 10000
```
