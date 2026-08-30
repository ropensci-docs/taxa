# Fill in NA values in sequence

Fill in the NA values in a ascending sequence based on nearby non-NA
values. Used to guess the order values for unknown ranks based on the
values of known ranks.

## Usage

``` r
impute_order_na(order, inc = 1)
```

## Arguments

- order:

  An ascending sequences, possibly with NAs

- inc:

  The increment size to use for values in NA blocks at the start and end
  of the sequence.
