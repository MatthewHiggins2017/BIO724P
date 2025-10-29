
# **Part 1 - Introduction to basic data structures**

----------------

## Introduction

You may already be familiar with R from introductions to statistics, and so some of the material covered here should be fairly straightforward. However, please work through all sections in order and there are harder bonus questions at the end! 

We will not be covering any stats in todays crash course as our goal is to bring you up to speed using R. Thoughout the day, make use of R’s help system and [https://chatgpt.com/](https://chatgpt.com/), your neighbour, and don't be afraid to ask a demonstrator for help if you are stuck!

-----------------------

## The environment

To start with, let us reacquaint ourselves with the R environment. First of all, launch R (or RStudio).

The main window you where you talk directly to R is called the **console**. This is where you run lines of code. Often, we prefer typing in a separate window in a separate file called a **script**. Try typing `1 + 2`` in this window and pressing return. Notice that no output is produced - the cursor just moves to the next line. This is because a script is fundamentally different from the console and in fact works just like any other **text editor**. In order to run the code that we have written in a script we need to select the line(s) that we want to run and hit Run, or type shift-enter or control-enter. This copies the selected line(s) over to the console and evaluates them in the order they are written. In this way we can create a long sequence of commands in a way that would not be possible by working directly in the console. Using a script also helps for keeping track of what we did. In general you should work mainly with scripts and limit your direct use of the console.

Also keep in mind that the R help is extremely good. Just put a question mark before any function that you do not understand (e.g. `?length`) to bring up the help file for that function. There are also many R websites and forums that you may find useful. The best way to learn any programming language is to fiddle - so please fiddle away with these tools to guide you!

-------------------

## Variables
A variable is a symbolic way of storing a particular set of values and/or characters. For example, try typing

```R
x <- 5
y <- 225
```
into the console and hitting return. This assigns the number `5` to the symbol `x`. You can run operations on variables (e.g. `3*x^2`), create new variables from existing variables (e.g. `y <- 3*x^2`), and reassign existing variables to a new value (e.g.` x <- 3*x^2`; try running that a few times).

Please always use `<-` for assignment. When in doubt about how to write something, check the [tidyverse style guide](https://style.tidyverse.org); it provides standard guidelines which most R users do or should follow.

You can name variables almost anything you want. Try using descriptive names (avoiding `x` and `y`), and using "_" to separate words. As a rule of thumb, remember to make your code easily understandable for other people, including your future self.

Finally some variable names are not allowed. Typing `?make.names` in the console brings up a help file describing the important variable name restrictions.

#### Q1. Create a new variable, `z`, out of the values in `x` and `y`. You can choose any formula you want for `z`, as long as it contains both `x` and `y`.


-------------------------

## Data classes
There are several classes (or types) of data.  The class of your data tells you whether R interprets the data as numbers, letters, factors (i.e. categories), logical values or a number of alternatives. You can use the function `class()` to check the class of a variable.

You will probably have seen numeric (`x <- 5`) and character variables (`x <- "hello"`). An important class of data that you might not be familiar with is **logical data**. Simply put, logical data can only take one of two possible values: `TRUE` or `FALSE`. There are a number of different ways of arriving at a logical variable. The most obvious is to simply define a variable as true, for example:

```R
x <- TRUE
```

or false, for example

```R
x <- FALSE
```

Try creating a logical variable in this way and look at the class of the variable - if you have done it correctly it should read "logical" (keep in mind that R is case-sensitive, i.e. `x <- false` will throw an error).

However, this is not the way that logical variables tend to be used in programming. We often create logical variables through a particular type of calculation, called a **logical expression**. You can think of a logical expression as a statement (or a question) that we send to R, which may be a true statement, or it may be a lie! For example, try evaluating the code

```R
5 > 4
```

This statement is clearly true and accordingly R returns a value `TRUE`. The statement

```R
5 < 4
```
on the other hand, returns the value `FALSE`. We can assign this logical value to a variable by using the logical expression as input to the variable. This sounds complicated, but in practice it is very simple. Take the example

```R
x <- (5 > 4)
```

You can read the expression above as "the variable x is assigned the outcome of the logical expression 5 > 4". In this particular example the variable `x` will get the value `TRUE`. Notice that the logical expression itself is within parentheses. This is not strictly required, but is good coding practice as it avoids confusion between the assignment symbol and the logical expression.

The main logical operators that you should be familiar with are the following:

* `>` is greater than
* `<` is less than
* `>=` is greater than or equal to
* `<=` is less than or equal to
* `==` is equal to
* `!=` is not equal to

Play around with some of these operators in your own made-up logical expressions. Make sure you are comfortable assigning a logical value to a variable.

We can create more sophisticated logical expressions using the "and" command and the "or" command. The "and" command is written `&` and called ampersand (keyboard shortcut Shift+7), while the "or" command is written `|` and called a "pipe" or vertical bar (keyboard shortcut Shift+\ on a standard Windows keyboard). These "operators" can be placed between two or more logical expressions - exactly as you would do in a spoken sentence. For example, the expression

```R
(x > 5) & (x <= 10)
```
can be read "x is greater than five, and x is less than or equal to ten". Similarly, the expression

```R
(x < 6) | (x == 12)
```

can be read "x is less than six, or x is equal to twelve". By using a combination of these operators, while making good use of parentheses, it is possible to come up with some quite complex statements.


**A short note on classes:**

It's easy to get numeric and character data confused. For example, in `x <- "blue"`, `x` is of class "character", while in `x <- 4`, `x` is of class "numeric". The problem comes if you type:

```R
x <- "4"
```

In this case `x` is of class "character" because of the quotation marks. Try typing `class(x)` if you are confused. You can also type `is.numeric(x)` and `is.character(x)`.



#### Q2. Let us define the variable `x <- 10`. What will the outcome of the following expressions be?

* `(x > 5)`
* `(x <= 10)`
* `(x != 10)`
* `(x < 5) & (x < 105)`
* `(x < 4) | (x > 14) | (x == 10)`

#### Q3. Below are some of the rules that logical operators follow. Write in plain English what it means.

* `TRUE & TRUE` is `TRUE`
* `TRUE & FALSE` is `FALSE`
* `FALSE & TRUE` is `FALSE`
* `TRUE | FALSE` is `TRUE`
* `FALSE | TRUE` is `TRUE`

#### Q4. Given three variables (`x`, `y` and `z`), how would you write the following sentence in a logical expression?

*The variable `x` is less than variable `y`, or greater than variable `z`?*

-------------------------------

## Scalars and vectors
Objects can be of different types. So far, we have looked at **scalar objects**, which contain a single variable (e.g. `x <- 3`). Another very common type of object is the **vector**, which is an object containing several elements:

```R
numeric_vec   <- c(1, 1, 2, 3, 5, 8)   # c is a function for combining values into a vector or list.
seq_vec1      <- seq(from = 10, to = 5) 
seq_vec2      <- seq(from = 0, to = 10, by = 0.25)
rep_vec       <- rep(x = 2, times = 12)
character_vec <- c("How", "Now", "Brown", "Cow")
logical_vec   <- c(TRUE, TRUE, FALSE, TRUE, TRUE, FALSE)
```

As you know by now, R is good at manipulating these vectors, with easy ways of accessing individual elements of a vector by using scalar objects as index (e.g. `x[3]`) and of applying simple operations on all elements of the vector (e.g. `vec1 * 3` or `vec1 * vec2` - *make sure you understand what R is doing here*). You can also use vectors to access a set of elements (e.g. `x[seq(from = 1, to = 5)]`) or specific elements (e.g. `x[c(2, 7, 9)]`) of a vector or variable. Remember that, for some calculations between different vectors, the vectors need to be compatible. This generally means they have lengths that are multiple of each other. Note that in R, the first position of a vector has the index 1, unlike in some other programming languages where the first position has the index 0.

#### Q5. What number would you obtain if you typed `seq_vec2[3]` in the console? (try working this out for yourself before typing it into R)
 
#### Q6. What happens when you type `seq_vec2[seq(from = 1, to = 5)]` in the console and hit return?

#### Q7. How would you retrieve just the 8th, 13th and 21st elements of `seq_vec2`?

Simple calculations can be performed on vectors, in which case the operation is applied to every element of the vector separately. For example, try typing

```R
numeric_vec_squared <- numeric_vec ^ 2
```

in the console. You will find that `numeric_vec_squared` contains values taken from `numeric_vec`, where each element has been squared individually. Similarly, you can create logical expressions that apply to the whole matrix, such as `numeric_vec > 3`

You can also perform operations involving several vectors, as long as the vectors have compatible lengths. For example, try typing

```R
combined_vec1 <- numeric_vec * seq_vec1
```

You will find that each of the elements of `combined_vec1` is equal to the product of the corresponding elements in `numeric_vec` and `seq_vec1`

#### Q8. Try evaluating `combined_vec2 <- numeric_vec * seq_vec2` in the console. What happens? Why?

#### Q9. What do you type to find the length of a vector?

#### Q10. In fact, compatible does not mean that vectors have to be exactly the same length. Try evaluating `combined_vec3 <- numeric_vec * rep_vec` in the console, and look at the result. What is the reasoning behind the values produced?


----------------------

## Matrices

Another major type of object in R is the **matrix**. A matrix is simply a rectangular grid of values. One of the simplest ways of producing a matrix is by combining several vectors through the functions `rbind()` and `cbind()`. Try `rbind(numeric_vec, seq_vec2)`.

#### Q11. What happens when you evaluate `rbind(numeric_vec, seq_vec2)`? What happens when you evaluate `cbind(numeric_vec, seq_vec2)`? Why?
#### Q12. When you evaluate `rbind(numeric_vec, seq_vec2)` you get a warning message. Why?
#### Q13. What happens when you evaluate `rbind(numeric_vec, rep_vec)`? Why?

You can also create matrices directly in a number of different ways:

```R
matrix1 <- matrix(data = seq_len(length.out = 24), nrow = 6, ncol = 4)
matrix2 <- matrix(data = seq_len(length.out = 24), nrow = 6, ncol = 4, byrow = TRUE)
matrix3 <- diag(x = 5, nrow = 3, ncol = 2)
matrix5 <- matrix(data = "Hello World", nrow = 2, ncol = 5)
```

As with vectors, you can get to the elements of a matrix using square brackets, but with a two-dimensional index, one for rows and another one for columns! For example:

 * `matrix1[4, 3]`
 * `matrix1[seq_len(length.out = 2), seq_len(length.out = 2)]`
 * `matrix1[seq_len(length.out = 2), ]`

#### Q14. How do you retrieve the 2nd column of `matrix2`?

You can perform simple calculations on matrices, in which case the calculation applies to each element separately:

```R
(matrix3 + 2) * 2
```
You can also combine the values in several matrices, as long as the dimensions of the matrices are compatible

```R
(matrix1 * 100) + matrix2
```

Finally, you can create logical expressions that apply to an entire matrix. For example, try evaluating:

```R
(matrix1 > 10)
```

There are a number of useful functions that can be applied to matrices. Have a look at each of the following functions, and try to make sense of the output:

* `length()`
* `dim()`
* `t()`
* `colSums()`
* `summary()`

Keep in mind that if you ever need help in understanding a function, just bring up the help file for that function.

#### Q15. The variable `matrix1` describes a matrix produced by the following code:

```R
matrix1 <- matrix(data = seq_len(length.out = 50), nrow = 10, ncol = 5)
```

What number would we expect to see when we evaluate `matrix1[1, 2]`? Try to answer this without evaluating the code! Why not a different number?

#### Q16. Which of these commands would output the 2nd and 4th columns of matrix1 only (again, try answering this without evaluating the code!)?

```R
matrix1[2, 4]
matrix1(, (2, 4))
matrix1[c(2, 4), ]
matrix1[, c(2, 4)]
```
** Note that in most situations, we try to avoid using this type of column indication. This is because it is easy to make a mistake with the numbers. Instead, it is easier and less risky to use column names **

#### Q17. Write your own script for creating a matrix from three separate vectors. The first vector, `vec1`, should be 50 elements long, and should simply contain the numbers 1 to 50. The second vector, `vec2`, should contain the square of these numbers (i.e. `vec1` raised to the power 2). The third vector, `vec3`, should contain the cube of these numbers (i.e. `vec1` raised to the power 3). Finally, create a matrix, `my_matrix`, which has `vec1` as the first row, `vec2` as the second row, and `vec3` as the third row.

----------------------

## Data frame
A very common type of object is the **data frame**. On the face of it, these look very similar to matrices. However, there are some important differences between data frames and matrices. The most important difference is that, in a matrix, all the elements need to be of the same class, while in a data frame, different classes are allowed. Several data frames are  loaded into R by default (e.g., `Puromycin`). Check the help to understand what this data includes: `?Puromycin`.

R allows you to get to specific columns using their name and the dollar sign: `Puromycin$rate`.  (it is also possible to use indices like in matrices, for example`Puromycin[1, 1]` or `Puromycin[, 2]`. But using indices is risky and should thus be avoided).

Note that, although the data frame is of class data frame, typing `Puromycin$rate` will return a vector of class numeric (try using the function `class()` to check this).

Normally, when R encounters columns with words in a data frame (rather than numbers), it automatically interprets them as data of a different type, the **factor** (this is true for R version 3, R version 4 interprets columns with words as data type **character**). This allows us to work with categorical data, by organising the data into discrete categories, known as levels (e.g., red, yellow and blue could be the levels of a column called ‘colour’). Type the following for an example:

```R
Puromycin$rate
class(Puromycin$rate)
class(Puromycin$state)
levels(Puromycin$state)
as.character(Puromycin$state)
```

----------------------

## Lists

The last data type that is commonly seen in R is the **list**. A list is a bit like a complicated vector, where the elements can be objects of any type. For example, we can make a list of vectors:

```R
my_list <- list(a = c(1, 2, 3), b = c(5, 6, 7, 8, 9, 10), d = c('G', 'H'))
```

Again, we can access elements from the list using their index, with brackets `my_list[[1]]`, *but you should NOT do this!*. Instead, use the names whenever possible, either using the bracket notation (`my_list[['a']]`) or the dollar sign (`my_list$a`). Lists can get very complex, since there is no limits on the data type of the elements. Therefore, you can get lists of vectors, lists of lists, lists of vectors and lists, etc…

There are other types of data in R, with many being specific to particular libraries.


--------------------------------------

## Subsetting a data frame
We have already come across one way of subsetting through the use of square brackets. By typing, for example,

```R
Puromycin
Puromycin[c(1, 2, 3), ]  # this is acceptable
Puromycin[, 2]           # never do this: use the column's name instead
```
we can isolate certain rows of the data frame that we are interested in. Using numbers to access specific rows is ok, but we should never do this with columns. Instead, we can use `subset` (see below) or the dollar sign `$` to get a specific column:

```R
Puromycin$rate
```

We can isolate data easily by using the logical statements mentioned above. For example, we can check which rows have a rate that is less than 100:

```R
# returns TRUE or FALSE
Puromycin$rate < 100
# returns which elements are TRUE
which(Puromycin$rate < 100)
```

We can use the subset function to select the rows for which the statement is TRUE:

```R
# returns all the columns, but only the rows for which
# Puromycin$rate < 100 is TRUE
puromycin_sub <- subset(Puromycin, rate < 100)
```

We could subset by the "state" column:

```R
puromycin_treated <- subset(Puromycin, subset = state == "treated")
```

This will return all fields for which the state is equal to "treated". Notice that the factor must be written in quotation marks here, as R needs to know that it is looking for a particular set of characters, rather than a variable.

#### Q18. How would you subset the variable `Puromycin` to return only those fields for which the concentration is greater than 0.1?
#### Q19. What is the average (mean) concentration for these cells?
#### Q20. How would you subset the variable `Puromycin` to return only the fields for which the cells were not treated?
#### Q21. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.5 and the rate is greater than 100 (remember the "and" command from logical expressions)?
#### Q22. How would you subset the variable `Puromycin` to return only the fields for which the concentration is greater than 0.2 and the cells have been treated?
#### Q23. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.1 or greater than 0.2?
#### Q24. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.2 and the rate is less than 70 and the cells have been treated?


--------------------------------------


# **Part 2 - Functions & Loops**

Building on your existing skills, we will now move on to consider advanced ways of controlling program flow. Specifically, we will explore **functions** and **loops**, two important features of R that are also present in most other programming languages. We will also be doing a few exercises with DNA/RNA strings. As always, you will want to refer frequently to the R help files (through `?`) and your own notes when exploring these new concepts.


----------------

## Functions

Functions are pieces of code that take input information (in the form of "arguments"), do something with it, and give back an output. They allow you to run an analysis multiple times without having to rewrite it from scratch every time you need to run it. A function looks like this:

```r
function_name <- function(input) {

  ### the "body" of the function

  # code that performs some calculation on the input
  # possibly other lines of code that perform calculations

  # returning an output vector:
  return(output)
}
```

You can choose whatever name you want instead of `function_name` (try a meaningful name). After the `<-`, the word `function` within brackets lets R know that you are writing a new function. Here, `input` is the name of the only argument that the calculations in the `body` of the function are based on (your function *can* have multiple arguments). Between the curly brackets `{}` is the main code of your function, where the calculation(s) happen. Almost everything that occurs between the curly brackets stays within the curly brackets. The only thing that comes outside the curly brackets is what you put into the `return()` on the last line. If you have no `return()`, your function may compute something but nobody will ever know about it! Note that the `return` command can only handle a single argument.

To take a self-explanatory example:

```r
x <- c(2, 3, 4, 5)
mean(x)
```

You just used the `mean` function, one of many functions that our predecessors built into R. The point of this function is that you can calculate the mean of any vector without explicitly writing the formula for the mean each time. The interesting thing about R is that it is possible to create your own functions. This is how R functions work:

```r
## Define function named 'my_own_mean'

my_own_mean <- function(numbers) {
  ## Calculate mean
  # Sum all numbers in the vector
  sum_of_values <- sum(numbers)

  # Obtain the number of values in the vector
  number_of_values <- length(numbers)

  # Get the mean
  mean_value <- sum_of_values/number_of_values

  ## Output the mean
  return(mean_value)
}

## Now run the function with some data:
my_own_mean(numbers = c(10, 20, 30, 40))

my_own_mean(numbers = seq(from = 1, to = 50))

```

We created a function that computes the sum and number of all values in a given vector (`numbers`) and then divides them to obtain the mean. We split the calculation in three steps, just to show that you can have many lines of code in the body of a function. The only input this function receives is a vector of numbers (`numbers`) and all the calculations are based on this. In the end we return the result of the third calculation (`mean_value`). Does `number_of_values` exist in the normal R console? No! Because this variable was only created within the curly brackets. Remember? What happens between the curly brackets stays in the curly brackets.

Nothing much happens after loading the function `my_own_mean` into R (you always have to evaluate the entire code of the function from `function_name` to the closing curly brackets `}` if you made changes to the code). The magic happens when you *call* the function. We did this by typing `my_own_mean(numbers = 1:50)` (of course you can use other vectors instead as well). The vector with numbers from 1 to 50 will be used as `numbers` in the function.

Now take a look at the following lines of code. This code is designed to take a number in seconds and convert it into hours, minutes, and remaining seconds (`floor()` is R's built-in function for rounding down to the closest whole number):

```r
# Input raw number of seconds
number_of_seconds <- 19955

# Convert number_of_seconds into hours, minutes, and seconds
hours   <- floor(number_of_seconds / (60 * 60))
minutes <- floor((number_of_seconds - hours * (60 * 60)) / 60)
seconds <- number_of_seconds - ((hours * 60) + minutes) * 60

# Create a single vector containing all three quantities
outputs <- c(hours, minutes, seconds)

# Output the solution to the console
outputs
```

#### Q25. Modify the code above to make it into a function called `time_converter`. This function should take a single number as an argument (the number of seconds we want to convert). This function should also include the three lines of code that convert `number_of_seconds` into `hours`, `minutes`, and `seconds`, the line of code that merges these three variables into one vector, and a line returning this vector as the output of the function. Once you created the function and loaded it into R, use relevant examples for testing (0, 3600, another). Remember to indent any code inside the curly brackets.


#### Q26. Write your own function for converting distances between different units. Your function should take the distance in kilometres as input and return the distance in miles as output ([1 kilometre is 0.6213712 miles](https://en.wikipedia.org/wiki/Mile)). Note: `floor` won't be needed in the calculations here. Remember to clearly comment/annotate your code and make appropriate use of whitespace including indentation and newlines.


------------------------------

### More complex functions

Functions can be very useful when you have to do the same calculation many times. We will now consider a hypothetical experiment in which we are measuring the flight speed of bees through flight tunnels.

We would like to measure the flight speed of the bees in meters per second. Annoyingly, the timer we used gave readings with the format `hours:minutes:seconds`, rather than just the total number of seconds.

Fortunately, functions in R can take more than one argument:

```r

my_function <- function(input1, input2, ...) {
    # code including input1, input2, ...
    return(something)
}

```

#### Q27. Make a function that takes `hours`, `minutes` and `seconds` as inputs, and outputs the total number of seconds. Make sure it has three arguments and a descriptive name. Test the function with a range of times for which you know the answer.

In our experiment, most bees flew through the test tunnel in under an hour. It is time consuming to include the argument `hours = 0` every time that we call the function.

A neat thing about functions is that we can set default values for any argument, using the syntax:

```r
my_function <- function(input1, ..., input15 = default) {
  # code including input1, input2, ..., input15
  return(something)
}
```

The default argument(s) is generally placed at the end of the argument list.

#### Q28. Make the `hours` and `minutes` arguments be defined as 0 by default in your function. Run the function without supplying these two arguments, then run it again with using a range of `hours` and `minutes`.

Finally, we would like to create a function to measure the flight speed of the bees in meters per second. This function should:

* Take the tunnel length (in meters), hours, minutes and seconds as arguments
* Use your previous function to convert hours, minutes and seconds to seconds
* Calculate the speed of the bees in meters per second
* Return the speed of the bees

#### Q29. Create this function. Test it with a control (values for which you know the answer).

#### Q30. Use the function to measure the speed of the bees with the following measurements:

Distance (m) | Time (hours:minutes:seconds)
---------|------
1 |00:00:08
10 |00:00:40
300 |00:05:00
800 |01:06:40

#### Q31. Can you think of parameter values that would make your function not work properly? What happens if you try running the function with these values?


-------------------------------------

### Functions with other types of input

Note that functions do not have to take single numbers as input. They can take vectors, matrices, data frames, or any other type of object, and they can also take character and logical data as well as numerical. For example, the `mean` function we used earlier took the vector `x <- c(2, 3, 4, 5)` as input, which is a single vector with four numbers.

#### Q32. Write a function that takes a vector of words as input and outputs the number of characters in the longest word. Hint: you are going to need to find out how R counts the number of characters in words and how it finds the maximum value in a vector - use an internet search engine!


------------------------------------

## Loops
Imagine that you need to run the function `time_converter` on different numbers. You could type `time_converter` many different times, each time with a different number. But now imagine you had to type that thousands of times. Not fun.

Fortunately, computers were built to perform same tasks over and over again many times. They do this using a construct called a *loop*. Although there are several types of loops, we are going to learn about the 'for loop'. It works this way:

```r
## For loop example
for (seconds in c(1000, 2000, 3000)) {
  time_in_hours <- time_converter(number_of_seconds = seconds)
  print(time_in_hours)
}
```

The variable `seconds` only exists within the loop. The loop will run 3 times. The first time, `seconds` will take the first value from the vector `(1000, 2000, 3000)`, i.e., `1000`. R will run through the loop, computing `time_in_hours` and printing it. When R starts running through the loop the second time, `seconds` will have the value `2000`, and the previously calculated `time_in_hours` will have been forgotten.  R will run through the loop, computing `time_in_hours` and printing it. The third time, same thing again, but `seconds` will start with the value `3000`.

### Slightly more complex loops
There are some interesting ways in which we can stretch our understanding of loops. First of all, it is important to recognise that the values that we are iterating over can be anything that goes in a vector. The vector can be defined outside the loop definition line:

```r
## Character based loop values
greetings <- c("Hey", "Hi", "Hello", "Aloha", "Howdy",
               "Yooooo!", "Wassup", "What's shakin?",
               "yello!", "Greetings",  "Dude, wake up!")
for (word in greetings) {
  print(paste(word, " - said the giggling frog", sep = " "))
}

## Sequential loop values
my_favourite_numbers <- c(42, 3.14, 7, 69, 6.626e-34, 1024, 4, 2.718281828, 666, 1.61803398, 99)

# set the cumulative sum at zero before the loop starts
cumulative_sum <- 0

for (value in my_favourite_numbers) {
  # print the sentence
  print(paste(value, "is my favourite number", sep = " "))

  # add favourite numbers, sequentially
  cumulative_sum <- cumulative_sum + value

  # print the cumulative sum
  print(paste("The sum of my favourite numbers is:", cumulative_sum, sep = " "))
}

## Looping through the positions of each element of the vector (the index, or position)
foods <- c("tempeh", "beyond", "beans", "tofu")
for (position in seq_len(length(foods))) {
  current_food <- foods[position]
  message("At position ", position, " we have ", current_food)
}

```

### Storing loop results

You will often want to do more than just print the loop results. For example, you may want to keep them in a separate variable. Check the following example. What does `phrases` look like after the 4th iteration?

```r
## Vector to loop through
practical_attributes <- c("great", "deeply distressing", "very long", "amazeballs!", "informative")

## Empty vector to store the loop results in
phrases <- c()

for (practical_attribute in practical_attributes) {
 phrase <- paste("This practical is", practical_attribute)
 # Add the loop result to end of the vector of results
 phrases <- append(phrases, phrase)
}
```

A different way of approaching a for loop is to loop through the positions of a vector, rather than the vector itself. In the following code, we also create a vector for the result with the same length as the vector that we are looping through. We then use the position to 'populate' it:

```r
## Vector to loop through
practical_attributes <- c("great", "deeply distressing", "very long", "amazeballs!", "informative")

## Vector with empty elements (as long as practical_attributes)
phrases <- rep("", times = length(practical_attributes))

## Loop through the position rather than the vector
for (position in 1:length(practical_attributes)) {

  ## Create phrase, getting attribute from practical_attributes[i]
  phrase <- paste("This practical is", practical_attributes[position])

  ## Add phrase to the right position of the results vector
  phrases[position] <- phrase
}
```

It is important to understand these two approaches with loops: looping through items vs. looping through positions. In some contexts it is easier to use the first approach; in other contexts the second is easier. Once you are comfortable with loops, have a go at the following task:


#### Q33. Write a loop that iterates over the colours red, green, blue, yellow, orange, purple, pink and prints out the position (i.e. the position of the colour in the vector) and the colour itself. This should be done in human-readable format (i.e. "the colour red is in position 1 in the vector", "the colour blue is in position 2 in the vector", and so on). Make sure to indent the code appropriately between the curly brackets.

-------------------

### Using loops

For the following exercice, imagine that instead of buying a coffee, you deposit the £2.50 you would have spent into a savings account. The account has an annual interest rate of 5%, which is deposited into the account. You do not take any money out of the account for 20 years.

#### Q34. Use a `for` loop to calculate how much money there is in the account after 20 years.

#### Q35. Create a plot showing the amount of money in the account for each year. Hint: If you have not already done so, you will need to create a vector to store the account balance for each year. You can use the base R function `plot()`, or, if you are feeling adventurous, install the "ggplot2" package and use that! See [https://ggplot2.tidyverse.org/articles/ggplot2.html](https://ggplot2.tidyverse.org/articles/ggplot2.html) for more information.


#### Q36. Write a loop that calculates the population size depending on the reproduction rate over a period of 20 years. Store the population value for each iteration of the loop in a separate vector. Use the information below to create your answer:

* Use a starting population size of 1000.
* Every year,
   * obtain a random reproduction rate (e.g., `reproduction_rate <- rnorm(n = 1, mean = 1, sd = 0.4)`.
   * Update the population size value accordingly.
   * Print a summary of what happened.
   * Store each year's population in an external vector.
* Once you have all the population sizes, plot them.

### Nested Loops

Another important way of extending loops is to consider nested loops - in other words, loops within other loops! Have a look at the following code:

```r
coffee <- c("latte", "cappuccino", "flat white", "cortado")
cafes   <- c("Infusion", "Ground", "Sugar Cube", "Foxcroft & Ginger", "Sweet")

for (drink in coffees) {
  print(paste("I'd like a", drink, "... Where can I go?"))
  for (the_place in cafes) {
    print(paste("You can go to", the_place, "to have a", drink))
  }
}
```

Here we have one loop (with position `the_place`) nested within another loop (with position `drink`). We have also defined the values that `the_place` and `drink` can take. With a pen and paper, determine what is the 1st line printed, and then what is the 10th line printed? Evaluate this code and try to make sense of the output. Fiddle around with the different elements of this code until you are comfortable with nested loops. Warning - loops require your computer to perform many operations, and as such it is quite easy to crash R using loops. A simple block of code evaluated 100,000 times amounts to quite a big job. If you want to force R to exit a loop part way through, simply press 'Esc' (or control-C). Nested loops are particularly hazardous!

#### Q37. Create a nested loop. The outer loop should iterate over the words "Angry", "Lazy", and "Happy". The inner loop should iterate over the words "birds", "dogs", and "horses". The code inside the inner loop should print out a vector containing the values of both loops (for example "Angry" and "birds" in the first instance).

#### Q38. Look again at the code you wrote in Q37. Did you sufficiently indent your code (like in the example of a nested loop above), so that it is easy to see which lines of code are executed at which point of the different loops? If not, DO IT NOW! And continue doing it for the next questions as well.


----------------------------------------------------------

# Part 3 - Bonus Questions


#### Bonus Q39. Write a function that converts a short DNA sequence of 15 bases (e.g. "ACCTGTCATCATCCC") to RNA and splits the string into codon triplets. You will need to:

  * replace T with U  (thymine with uracil to convert DNA to RNA)
  * use `substring()` to split the sequence into triplets and `seq()` within `substring()`
  * return the RNA triplets string

Note `substring()` takes a 'first' and 'last' argument. The 'first' would be a sequence indicating where the beginnings of your triplets are. The 'last' argument would be a sequence indicating where the ends of your triplets are.  In `seq()` you will also indicate you want triplets.

As an example:

```r
dna_string <- c("AAATTT")
substring(dna_string, seq(from = 1, to = 4, by = 3), seq(from = 3, to = 6, by = 3))
```


#### Bonus Q40. Write a function to obtain the reverse-complement of a DNA sequence.

You can use this sequence (copy and paste it into R): `"ATTACGACGCGATTCCCGGTTAATCGAATTCCCA"`. As an example, the reverse-complement of ATGC is GCAT.

The tricky part here is reversing a single string of characters. Search around for `strsplit`.  You will need to:

* replace bases with their complement (you can use `gsub`, judiciously replacing uppercase characters with lowercase characters (or vice-versa)).
* split the string of DNA bases into separate characters with `strsplit`. Unfortunately, `strsplit` confusingly returns a list, so you will need to use `unlist()` to obtain a string again.
* reverse the sequence.
* remove the spaces to get your single string of DNA bases (look into the help files for the `paste()` function).
* return the reverse-complement sequence.

#### Bonus Q41. Write a function that assesses whether a given word or phrase is a palindrome.

Palindromes are arrangements of words or letters which read the same way whether you read them backwards or forwards, such as the phrase *never odd or even* (if you remove the spaces). In molecular biology, many restriction enzyme sites are palindromic.

Before starting to code, think about the steps that you would need to go through in order to judge if something is a mirror palindrome:

 * Write these steps as comments in an R script window (or a piece of paper) , then think about how you can tell the computer to execute those steps.
 * Only start writing the code when you have a plan of what you want to do.
 * Write your code as a one-off first - without considering that you'll do a function.
 * Only once you're happy with how things work, sandwich your code into a function format.
 * Use easy test cases where you know the answer in order to check that your function works.
 * The `strsplit` helpsheet is particularly interesting in relation to this question.

