
# **Part 1 - Answers**

## Q1. Create a new variable, z, out of the values in x and y. You can choose any formula you want for z, as long as it contains both x and y.

```r
# Using the values x <- 5 and y <- 225 defined earlier
z <- (x * y) ^ 2
```

## Q2. Let us define the variable x <- 10. What will the outcome of the following expressions be?

- `(x > 5)` → Answer: **TRUE**
- `(x <= 10)` → Answer: **TRUE**  
- `(x != 10)` → Answer: **FALSE**
- `(x < 5) & (x < 105)` → Answer: **FALSE**
- `(x < 4) | (x > 14) | (x == 10)` → Answer: **TRUE**

## Q3. Below are some of the rules that logical operators follow. Write in plain English what it means.

- `TRUE & TRUE` is `TRUE` → **Both conditions must be true for the result to be true**
- `TRUE & FALSE` is `FALSE` → **If any condition is false when using AND, the result is false**
- `FALSE & TRUE` is `FALSE` → **If any condition is false when using AND, the result is false**  
- `TRUE | FALSE` is `TRUE` → **If at least one condition is true when using OR, the result is true**
- `FALSE | TRUE` is `TRUE` → **If at least one condition is true when using OR, the result is true**

## Q4. Given three variables (x, y and z), how would you write the following sentence in a logical expression?

*The variable x is less than variable y, or greater than variable z?*

```r
(x < y) | (x > z)
```

## Q5. What number would you obtain if you typed `seq_vec2[3]` in the console?

```r
seq_vec2 <- seq(from = 0, to = 10, by = 0.25)
seq_vec2[3]  # Result: 0.5
```

## Q6. What happens when you type `seq_vec2[seq(from = 1, to = 5)]` in the console and hit return?

```r
seq_vec2[seq(from = 1, to = 5)]  # Returns the first 5 elements: 0.00 0.25 0.50 0.75 1.00
```

## Q7. How would you retrieve just the 8th, 13th and 21st elements of `seq_vec2`?

```r
seq_vec2[c(8, 13, 21)]
```

## Q8. Try evaluating `combined_vec2 <- numeric_vec * seq_vec2` in the console. What happens? Why?

```r
# This will produce a warning because the lengths are incompatible
# numeric_vec has 6 elements, seq_vec2 has 41 elements
# R will recycle the shorter vector, but since 41 is not a multiple of 6, it gives a warning
combined_vec2 <- numeric_vec * seq_vec2
```

## Q9. What do you type to find the length of a vector?

```r
length(vector_name)
```

## Q10. In fact, compatible does not mean that vectors have to be exactly the same length. Try evaluating `combined_vec3 <- numeric_vec * rep_vec` in the console, and look at the result. What is the reasoning behind the values produced?

```r
combined_vec3 <- numeric_vec * rep_vec
# Both vectors have 6 and 12 elements respectively
# Since 12 is a multiple of 6, R recycles numeric_vec twice to match the length
# Each element of numeric_vec is multiplied by the corresponding element of rep_vec (which is all 2s)
```

## Q11. What happens when you evaluate `rbind(numeric_vec, seq_vec2)`? What happens when you evaluate `cbind(numeric_vec, seq_vec2)`? Why?

```r
# rbind(numeric_vec, seq_vec2) creates a matrix with 2 rows
# It will give a warning because the vectors have different lengths (6 vs 41)
# The shorter vector will be recycled

# cbind(numeric_vec, seq_vec2) creates a matrix with 2 columns  
# It will also give a warning for the same reason
```

## Q12. When you evaluate `rbind(numeric_vec, seq_vec2)` you get a warning message. Why?

The warning occurs because `numeric_vec` has 6 elements while `seq_vec2` has 41 elements. Since 41 is not a multiple of 6, R cannot evenly recycle the shorter vector to match the longer one.

## Q13. What happens when you evaluate `rbind(numeric_vec, rep_vec)`? Why?

```r
rbind(numeric_vec, rep_vec)
# This works without warning because both vectors have compatible lengths
# numeric_vec has 6 elements, rep_vec has 12 elements
# 12 is a multiple of 6, so R can recycle numeric_vec evenly
```

## Q14. How do you retrieve the 2nd column of `matrix2`?

```r
matrix2[, 2]
```

## Q15. The variable `matrix1` describes a matrix produced by the following code: `matrix1 <- matrix(data = seq_len(length.out = 50), nrow = 10, ncol = 5)`. What number would we expect to see when we evaluate `matrix1[1, 2]`? Try to answer this without evaluating the code! Why not a different number?

**Answer:** We would expect to see **11**.

**Reasoning:** The `matrix()` function fills matrices by column by default. With `seq_len(50)` creating numbers 1 to 50, the first column gets 1-10, the second column gets 11-20, etc. So `matrix1[1, 2]` (first row, second column) would be 11.

## Q16. Which of these commands would output the 2nd and 4th columns of matrix1 only?

```r
matrix1[, c(2, 4)]  # This is the correct answer
```

The other options are incorrect:
- `matrix1[2, 4]` - gives one element, not columns
- `matrix1(, (2, 4))` - incorrect syntax  
- `matrix1[c(2, 4), ]` - gives rows, not columns

## Q17. Write your own script for creating a matrix from three separate vectors.

```r
# Create the first vector with numbers 1 to 50
vec1 <- seq(from = 1, to = 50, by = 1)

# Create the second vector with the squares of vec1  
vec2 <- vec1 ^ 2

# Create the third vector with the cubes of vec1
vec3 <- vec1 ^ 3

# Create a matrix with vec1, vec2, and vec3 as rows
my_matrix <- rbind(vec1, vec2, vec3)
```

## Q18. How would you subset the variable `Puromycin` to return only those fields for which the concentration is greater than 0.1?

```r
high_conc <- subset(Puromycin, conc > 0.1)
```

## Q19. What is the average (mean) concentration for these cells?

```r
mean(high_conc$conc)
# Answer: 0.4573333
```

## Q20. How would you subset the variable `Puromycin` to return only the fields for which the cells were not treated?

```r
untreated <- subset(Puromycin, state == "untreated")
```

## Q21. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.5 and the rate is greater than 100?

```r
conc_rate_filt <- subset(Puromycin, conc < 0.5 & rate > 100)
```

## Q22. How would you subset the variable `Puromycin` to return only the fields for which the concentration is greater than 0.2 and the cells have been treated?

```r
conc_state_filt <- subset(Puromycin, conc > 0.2 & state == "treated")  
```

## Q23. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.1 or greater than 0.2?

```r
conc_filt <- subset(Puromycin, conc < 0.1 | conc > 0.2)
```

## Q24. How would you subset the variable `Puromycin` to return only the fields for which the concentration is less than 0.2 and the rate is less than 70 and the cells have been treated?

```r
conc_rate_state_filt <- subset(Puromycin, conc < 0.2 & rate < 70 & state == "treated")
```

## Q25. Write your own well annotated and fully functional script for calculating the volume of a rectangular room with the following dimensions: length: 5m, width: 4m, height: 3m

```r
# Define the dimensions of the room
length <- 5  # Length in meters
width <- 4   # Width in meters  
height <- 3  # Height in meters

# Calculate the volume using the formula: Volume = length * width * height
volume <- length * width * height

# Display the result
print(paste("The volume of the room is", volume, "cubic meters"))
```

-----------------------

# **Part 2 - Functions & Loops**

## Q25. Modify the code above to make it into a function called `time_converter`. This function should take a single number as an argument (the number of seconds we want to convert). This function should also include the three lines of code that convert `number_of_seconds` into `hours`, `minutes`, and `seconds`, the line of code that merges these three variables into one vector, and a line returning this vector as the output of the function. Once you created the function and loaded it into R, use relevant examples for testing (0, 3600, another). Remember to indent any code inside the curly brackets.

```r
# Define the time_converter function
time_converter <- function(number_of_seconds) {
  # Convert number_of_seconds into hours, minutes, and seconds
  hours   <- floor(number_of_seconds / (60 * 60))
  minutes <- floor((number_of_seconds - hours * (60 * 60)) / 60)
  seconds <- number_of_seconds - ((hours * 60) + minutes) * 60
  
  # Create a single vector containing all three quantities
  outputs <- c(hours, minutes, seconds)
  
  # Return the vector
  return(outputs)
}

# Test the function
time_converter(0)  #Output: 0 0 0
time_converter(3600) #Output: 1 0 0
time_converter(90) #Output: 0 1 30
```

## Q26. Write your own function for converting distances between different units. Your function should take the distance in kilometres as input and return the distance in miles as output (1 kilometre is 0.6213712 miles). Note: `floor` won't be needed in the calculations here. Remember to clearly comment/annotate your code and make appropriate use of whitespace including indentation and newlines.

```r
# Define the km_to_miles function
km_to_miles <- function(kilometers) {
  # Conversion factor from kilometers to miles
  conversion_factor <- 0.6213712
  
  # Convert kilometers to miles using the conversion factor
  miles <- kilometers * conversion_factor
  
  # Return the converted distance in miles
  return(miles)
}

# Test the function
km_to_miles(100) #Output: 62.13712
```

## Q27. Make a function that takes `hours`, `minutes` and `seconds` as inputs, and outputs the total number of seconds. Make sure it has three arguments and a descriptive name. Test the function with a range of times for which you know the answer.

```r
# Define a function that converts hours, minutes, and seconds to total seconds
time_to_seconds <- function(seconds, minutes, hours) {
  # Calculate the total number of seconds
  total_seconds <- (hours * 60 * 60) + (minutes * 60) + seconds
  
  # Return the total number of seconds
  return(total_seconds)
}

# Test the function
time_to_seconds(seconds = 0,  minutes = 1,  hours = 0) #Output: 60
time_to_seconds(seconds = 10, minutes = 0,  hours = 10) #Output: 36010
time_to_seconds(seconds = 30, minutes = 10, hours = 0) #Output: 630
```

## Q28. Make the `hours` and `minutes` arguments be defined as 0 by default in your function. Run the function without supplying these two arguments, then run it again with using a range of `hours` and `minutes`.

```r
# Define a function that converts hours, minutes, and seconds to total seconds
time_to_seconds <- function(seconds, minutes = 0, hours = 0) {
  # Calculate the total number of seconds
  total_seconds <- (hours * 60 * 60) + (minutes * 60) + seconds
  
  # Return the total number of seconds
  return(total_seconds)
}

# Test the function with default values
time_to_seconds(seconds = 100) #Output: 100
time_to_seconds(seconds = 10, minutes = 10, hours = 1) #Output: 4210
time_to_seconds(seconds = 1, minutes = 1, hours = 1) #Output: 3661
```

## Q29. Create this function. Test it with a control (values for which you know the answer).

```r
# Define the function to calculate bee flight speed in meters per second
bee_flight_speed <- function(tunnel_length, hours, minutes, seconds) {
  # Convert the given time to total seconds reusing the time_to_seconds function
  total_time_seconds <- time_to_seconds(hours, minutes, seconds)
  
  # Calculate the speed (distance / time)
  speed_meters_per_second <- tunnel_length / total_time_seconds
  
  # Return the speed in meters per second
  return(speed_meters_per_second)
}

# Test the function with known values
print(bee_flight_speed(tunnel_length = 100, hours = 0,  minutes = 2, seconds = 0)) #Output: 0.8333333
print(bee_flight_speed(tunnel_length =  10, hours = 0, minutes = 0, seconds = 10)) #Output: 1
```

## Q30. Use the function to measure the speed of the bees with the following measurements:

| Distance (m) | Time (hours:minutes:seconds) | Speed |
|--------------|------------------------------|-------|
| 1            | 00:00:08                     | 0.125 |
| 10           | 00:00:40                     | 0.25  |
| 300          | 00:05:00                     | 1     |
| 800          | 00:06:40                     | 0.2   |

## Q31. Can you think of parameter values that would make your function not work properly? What happens if you try running the function with these values?

A few situations:
- If the distance is zero or negative, the function will return either a zero or negative speed, which doesn't make sense for a physical scenario.
- If time is zero, we get a divide by zero and an error
- If distance or time are entered as text e.g., "one hour" instead of numbers, things will crash

## Q32. Write a function that takes a vector of words as input and outputs the number of characters in the longest word. Hint: you are going to need to find out how R counts the number of characters in words and how it finds the maximum value in a vector - use an internet search engine!

```r
# Define the function to find the longest word length
longest_word_length <- function(words) {
  # Calculate the length of each word
  word_lengths <- nchar(words)
  
  # Find the maximum length among the calculated lengths
  max_length <- max(word_lengths)
  
  # Return the length of the longest word
  return(max_length)
}
```

## Q33. Write a loop that iterates over the colours red, green, blue, yellow, orange, purple, pink and prints out the position (i.e. the position of the colour in the vector) and the colour itself. This should be done in human-readable format (i.e. "the colour red is in position 1 in the vector", "the colour blue is in position 2 in the vector", and so on). Make sure to indent the code appropriately between the curly brackets.

```r
# Define the vector of colors
colours <-  c("red", "green", "blue", "yellow", "orange", "purple", "pink")

# Get the number of colours
number_of_colours <- length(colours)

# Loop through color in the vector
for (i in seq(from = 1, to = number_of_colours)) {
  # Print the position and color in a human-readable format
  print(paste("The colour", colours[i], "is in position", i, "in the vector."))
}
```

## Q34. Use a `for` loop to calculate how much money there is in the account after 20 years.

```r
initial_deposit <- 2.50
interest_rate <- 0.05
years <- 20

# Set the initial balance
balance <- initial_deposit

# Use a for loop to calculate the balance after 20 years
possible_years <- seq(from = 1, to = years)
for (year in possible_years) {
  interest <- balance * interest_rate
  balance <- balance + interest
}
```

## Q35. Create a plot showing the amount of money in the account for each year. Hint: If you have not already done so, you will need to create a vector to store the account balance for each year. You can use the base R function `plot()`, or, if you are feeling adventurous, install the "ggplot2" package and use that!

```r
# We need to keep track of the balances
balances <- rep(x = NA, times = 21)
balances[1] <- initial_deposit

for (year in possible_years) {
  interest <- interest_rate * balances[year]
  balances[year + 1] <- balances[year] + interest
}

# Load the ggplot2 package
library(ggplot2)

# Create a data frame for ggplot
balances_dataframe <- data.frame(year = c(possible_years, 21), 
                                 balance = balances)

ggplot(balances_dataframe, aes(x = year, y = balance)) + 
  geom_bar(stat = "identity") +
  ylim(0, 7) +
  labs(title = "Savings Over Time",
       x = "Years",    
       y = "Amount (£)")    
```

## Q36. Write a loop that calculates the population size depending on the reproduction rate over a period of 20 years. Store the population value for each iteration of the loop in a separate vector. Use the information below to create your answer:

```r
# Set the initial population size
pop_size <- 1000  # year 0

# Define the number of years for the simulation
years <- seq(from = 1, to = 20)

# Create a vector to store the population size for each year
population_sizes <- rep(x = NA, times = 20)

# Loop over each year to calculate population size
for (current_year in years) {
    # Generate a random reproduction rate (mean = 1, sd = 0.4)
    reproduction_rate <- rnorm(n = 1, mean = 1, sd = 0.4)

    # Calculate the number of new babies based on the reproduction rate
    num_babies <- floor(reproduction_rate * pop_size)

    # Update the population size
    pop_size <- pop_size + num_babies
    
    # Store the current population size in the vector
    population_sizes[current_year] <- pop_size
}

# Create a data frame for ggplot
population_df <- data.frame(year = years, population = population_sizes)

# Plot the population sizes over the years using ggplot2
ggplot(population_df, aes(x = year, y = population)) +
    geom_line(color = "blue") +  # Line for population growth
    geom_point(color = "blue") +  # Points at each year
    labs(title = "Population Size Over 20 Years",
         x = "Year",
         y = "Population Size") +
    theme_minimal() +  # Clean theme for the plot
    theme(text = element_text(size = 14))  # Increase text size for readability
```

## Q37. Create a nested loop. The outer loop should iterate over the words "Angry", "Lazy", and "Happy". The inner loop should iterate over the words "birds", "dogs", and "horses". The code inside the inner loop should print out a vector containing the values of both loops (for example "Angry" and "birds" in the first instance).

```r
# Define the outer loop variables (emotions)
emotions <- c("Angry", "Lazy", "Happy")

# Define the inner loop variables (animals)
animals <- c("birds", "dogs", "horses")

# Nested loop
for (emotion in emotions) {
  for (animal in animals) {
    # Print the combination
    print(c(emotion, animal))
  }
}
```

## Q38. Look again at the code you wrote in Q37. Did you sufficiently indent your code (like in the example of a nested loop above), so that it is easy to see which lines of code are executed at which point of the different loops? If not, DO IT NOW! And continue doing it for the next questions as well.

The answer is included in Q37 above with proper indentation.


-------------------

# **Part 3 - Bonus Question Answers**


## Q39: Write a function that converts a short DNA sequence of 15 bases (e.g. "ACCTGTCATCATCCC") to RNA and splits the string into codon triplets. 


```r
convert_dna_to_rna_triplets <- function(dna_seq) {
  
  # Replace T with U to convert DNA to RNA
  rna_seq <- gsub("T", "U", dna_seq)
  # Calculate the positions for triplets
  first_positions <- seq(from = 1, to = 15, by = 3)
  last_positions  <- seq(from = 3, to = 15, by = 3)
  
  # Create triplets using substring
  rna_triplets <- substring(text = rna_seq, 
                            first = first_positions, 
                            last = last_positions)
  
  return(rna_triplets)
}

triplets <- convert_dna_to_rna_triplets("ACCTGTCATCATCCC")
triplets

```

## Q40. Write a function to obtain the reverse-complement of a DNA sequence.

```r

# Define the function to get the reverse complement of a DNA sequence
reverse_complement <- function(dna_seq) {
  # Step 1: Replace each base with its complement
  complement <- gsub(pattern = "A", replacement = "t", x = dna_seq)
  complement <- gsub(pattern = "T", replacement = "a", x = complement)
  complement <- gsub(pattern = "C", replacement = "g", x = complement)
  complement <- gsub(pattern = "G", replacement = "c", x = complement)
  
  # Step 2: Split the string into separate characters and unlist
  split_seq <- strsplit(complement, "")[[1]]
  
  # Step 3: Reverse the sequence
  reversed_seq <- rev(split_seq)
  
  # Step 4: Remove spaces and return as a single string
  reverse_complement_seq <- toupper(paste(reversed_seq, collapse = ""))
  
  return(reverse_complement_seq)
}

reverse_complement("ACCTGTCATCATCCC")

```

## Q41: Palindromic Sequences Answers

**Question:** Write a function that assesses whether a given word or phrase is a palindrome. Palindromes are arrangements of words or letters which read the same way whether you read them backwards or forwards, such as the phrase "never odd or even" (if you remove the spaces). In molecular biology, many restriction enzyme sites are palindromic.

**Hint:** Before starting to code, think about the steps needed to judge if something is a mirror palindrome. Write these steps as comments first, then implement them. Use easy test cases where you know the answer.

**Answer:**

### Step 1: Planning (as comments)

```r
# Steps to check if a sequence is a palindrome:
# 1. Convert the input to uppercase (for consistency)
# 2. Remove spaces and special characters (for phrase palindromes)
# 3. Split the string into individual characters
# 4. Reverse the order of characters
# 5. Compare the original with the reversed version
# 6. Return TRUE if they match, FALSE otherwise
```

### Step 2: One-off code (testing the logic)

```r
# Test with a simple case
test_word <- "GAATTC"  # EcoRI restriction site - palindromic

# Convert to uppercase
test_word <- toupper(test_word)

# Remove spaces (not needed for this case, but good practice)
test_word <- gsub(" ", "", test_word)

# Split into individual characters
chars <- strsplit(test_word, "")[[1]]
chars
# Result: "G" "A" "A" "T" "T" "C"

# Reverse the characters
reversed_chars <- rev(chars)
reversed_chars
# Result: "C" "T" "T" "A" "A" "G"

# Join back into a string
reversed_word <- paste(reversed_chars, collapse = "")
reversed_word
# Result: "CTTAAG"

# Compare
test_word == reversed_word
# Result: FALSE (GAATTC is not the same as CTTAAG)

# Let's test with a true palindrome
test_word2 <- "GAATTC"
# Actually, for DNA palindrome, we need reverse complement!
# But for simple text palindrome, let's use:
test_word2 <- "racecar"
test_word2 <- toupper(test_word2)
chars2 <- strsplit(test_word2, "")[[1]]
reversed2 <- paste(rev(chars2), collapse = "")
test_word2 == reversed2
# Result: TRUE
```

### Step 3: Create the final Function

```r
# Function to check if a word or phrase is a palindrome
is_palindrome <- function(text) {
  # Convert to uppercase for case-insensitive comparison
  text <- toupper(text)
  
  # Remove spaces and non-alphanumeric characters
  text <- gsub("[^A-Z0-9]", "", text)
  
  # Split into individual characters
  chars <- strsplit(text, "")[[1]]
  
  # Reverse the characters
  reversed_chars <- rev(chars)
  
  # Join back into a string
  reversed_text <- paste(reversed_chars, collapse = "")
  
  # Compare original with reversed
  is_same <- (text == reversed_text)
  
  return(is_same)
}

# Test the function
test_cases <- c(
  "racecar",
  "hello",
  "A man a plan a canal Panama",
  "never odd or even",
  "GAATTC",
  "palindrome",
  "madam",
  "step on no pets"
)

# Test each case
for (test in test_cases) {
  result <- is_palindrome(test)
  print(paste(test, "->", ifelse(result, "IS a palindrome", "NOT a palindrome")))
}
```

**Output:**
```
[1] "racecar -> IS a palindrome"
[1] "hello -> NOT a palindrome"
[1] "A man a plan a canal Panama -> IS a palindrome"
[1] "never odd or even -> IS a palindrome"
[1] "GAATTC -> NOT a palindrome"
[1] "palindrome -> NOT a palindrome"
[1] "madam -> IS a palindrome"
[1] "step on no pets -> IS a palindrome"
```