151024 strings_and_factors
================
2024-10-15

# Let’s do strings

Rather than creating dataframe, just create vectors (for now just
understanding strings at a small scale), then see how it functions in
tidyverse later

Here saying that vector is just 4 words, and try to find specific
matches inside. Asking for string variable that im looking in a

``` r
string_vec = c("my", "name", "is", "jeff")

str_detect(string_vec, "a")
```

    ## [1] FALSE  TRUE FALSE FALSE

``` r
string_vec = c("my", "name", "is", "jeff")

str_detect(string_vec, "Jeff")
```

    ## [1] FALSE FALSE FALSE FALSE

``` r
string_vec = c("my", "name", "is", "jeff")

str_detect(string_vec, " jeff")
```

    ## [1] FALSE FALSE FALSE FALSE

See how the detect is very very specific

Can also replace

``` r
string_vec = c("my", "name", "is", "jeff")

str_detect(string_vec, " jeff")
```

    ## [1] FALSE FALSE FALSE FALSE

``` r
str_replace(string_vec, "e", "E")
```

    ## [1] "my"   "namE" "is"   "jEff"

``` r
string_vec = c(
  "i think we all rule for participating",
  "i think i have been caught",
  "i think this will be quite fun actually",
  "it will be fun, i think"
  )

str_detect(string_vec, "i think")
```

    ## [1] TRUE TRUE TRUE TRUE

since they all have i think, but want to find i think that starts with i
think

``` r
string_vec = c(
  "i think we all rule for participating",
  "i think i have been caught",
  "i think this will be quite fun actually",
  "it will be fun, i think"
  )

str_detect(string_vec, "^i think")
```

    ## [1]  TRUE  TRUE  TRUE FALSE

^ indicates beginning of a line

``` r
string_vec = c(
  "i think we all rule for participating",
  "i think i have been caught",
  "i think this will be quite fun actually",
  "it will be fun, i think"
  )

str_detect(string_vec, "i think$")
```

    ## [1] FALSE FALSE FALSE  TRUE

\$ indicates end of the line

``` r
string_vec = c(
  "Time for a Pumpkin Spice Latte!",
  "went to the #pumpkinpatch last weekend",
  "Pumpkin Pie is obviously the best pie",
  "SMASHING PUMPKINS -- LIVE IN CONCERT!!"
  )

str_detect(string_vec,"[Pp]umpkin")
```

    ## [1]  TRUE  TRUE  TRUE FALSE

Allow for two different options for what we are looking for

Looking for a pattern here: a number followed by two letters –\>

``` r
string_vec = c(
  '7th inning stretch',
  '1st half soon to begin. Texas won the toss.',
  'she is 5 feet 4 inches tall',
  '3AM - cant sleep :('
  )

str_detect(string_vec, "[0-9]")
```

    ## [1] TRUE TRUE TRUE TRUE

``` r
str_detect(string_vec, "[0-4]")
```

    ## [1] FALSE  TRUE  TRUE  TRUE

``` r
str_detect(string_vec, "[0-9][a-z]")
```

    ## [1]  TRUE  TRUE FALSE FALSE

``` r
str_detect(string_vec, "[0-9][a-zA-Z]")
```

    ## [1]  TRUE  TRUE FALSE  TRUE

We want to detect 7 followed by any character then 11 The character .
matches anything.

``` r
string_vec = c(
  'Its 7:11 in the evening',
  'want to go to 7-11?',
  'my flight is AA711',
  'NetBios: scanning ip 203.167.114.66'
  )

str_detect(string_vec, "7.11")
```

    ## [1]  TRUE  TRUE FALSE  TRUE

Not the one in the middle since there is no character seperating the 7
and 11 Suppose we are looking for a bracket which is usually used as
special characters, have special seperate meaning in regular expression

str_detect(string_vec, “\[”) \<– this will give

Put twp backslashs before the special character

``` r
string_vec = c(
  'The CI is [2, 5]',
  ':-]',
  ':-[',
  'I found the answer on pages [6-7]'
  )

str_detect(string_vec, "\\[")
```

    ## [1]  TRUE FALSE  TRUE  TRUE

# Factors

Emphasis numeric structures is want to convert to a numeric variable

``` r
sex_vec = factor(c("male", "male", "female", "female"))

as.numeric(sex_vec)
```

    ## [1] 2 2 1 1

See that there are levels

See that we get 2 2 1 1 out since it starts at alphabetical female level
first

Now change the underlying structure, so that male comes first.
Releveling

``` r
sex_vec = fct_relevel(sex_vec, "male")

as.numeric(sex_vec)
```

    ## [1] 1 1 2 2

Can find all lots of things to do in the “str\_” package can search in
console str\_ fct\_ package also to see what i can do with factors
