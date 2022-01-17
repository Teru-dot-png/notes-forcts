## [What is computer science?](https://cs50.harvard.edu/x/2022/notes/0/#what-is-computer-science)

-   Computer science is fundamentally problem solving, but we’ll need to be precise and methodical.
-   We can think of **problem solving** as the process of taking some input (a problem we want to solve) and generate some output (the solution to our problem).  
    ![word "input", arrow into box, arrow out of box, word "output"](https://cs50.harvard.edu/x/2022/notes/0/input_output.png)
-   To begin doing that, we’ll need a way to represent inputs and outputs, so we can store and work with information in a standardized way.
-   To represent letters, all we need to do is decide how numbers map to letters. Some humans, many years ago, collectively decided on a standard mapping of numbers to letters.

## [Algorithms](https://cs50.harvard.edu/x/2022/notes/0/#algorithms)

-   Now that we can represent inputs and outputs, we can work on problem solving. The black box that transforms inputs to outputs contains **algorithms**, step-by-step instructions for solving problems:  
    ![box with word "algorithms"](https://cs50.harvard.edu/x/2022/notes/0/algorithms.png)
-   We might have an application on our phones that store our contacts, with their names and phone numbers sorted alphabetically. The old-school equivalent might be a phone book, a printed copy of names and phone numbers.
-   We might open the book and start from the first page, looking for a name one page at a time. This algorithm would be correct, since we will eventually find the name if it’s in the book.
-   We might flip through the book two pages at a time, but this algorithm will not be correct since we might skip the page with our name on it.
-   Another algorithm would be opening the phone book to the middle, decide whether our name will be in the left half or right half of the book (because the book is alphabetized), and reduce the size of our problem by half. We can repeat this until we find our name, dividing the problem in half each time.
-   We can visualize the efficiency of each of those algorithms with a chart:  
    ![chart with: "size of problem" as x-axis; "time to solve" as y-axis; red, steep straight line from origin to top of graph labeled "n"; yellow, less steep straight line from origin to top of graph labeled "n/2"; green, curved line that gets less and less steep from origin to right of graph labeled "log_2  n"](https://cs50.harvard.edu/x/2022/notes/0/time_to_solve.png)
    -   Our first algorithm, searching one page at a time, can be represented by the red line: our time to solve increases linearly as the size of the problem increases. _n_ is a number representing the size of the problem, so with _n_ pages in our phone books, we have to take up to _n_ steps to find a name.
    -   The second algorithm, searching two pages at a time, can be represented by the yellow line: our slope is less steep, but still linear. Now, we only need (roughly) _n_ / 2 steps, since we flip two pages at a time.
    -   Our final algorithm, dividing the phone book in half each time, can be represented by the green line, with a fundamentally different relationship between the size of the problem and the time to solve it. If the phone book doubled in size from 1000 to 2000 pages, we would only need one more step to find our name.

## [Pseudocode](https://cs50.harvard.edu/x/2022/notes/0/#pseudocode)

-   We can write **pseudocode**, which is a representation of our algorithm in precise English (or some other human language):
    
    1  Pick up phone book
    2  Open to middle of phone book
    3  Look at page
    4  If person is on page
    5      Call person
    6  Else if person is earlier in book
    7      Open to middle of left half of book
    8      Go back to line 3
    9  Else if person is later in book
    10     Open to middle of right half of book
    11     Go back to line 3
    12 Else
    13     Quit
    
    -   With these steps, we check the middle page, decide what to do, and repeat. If the person isn’t on the page, and there’s no more pages in the book left, then we stop. And that final case is particularly important to remember. When programs or code don’t include that final case, they might appear to freeze or stop responding, or continue to repeat the same work over and over without making any progress.
-   Some of these lines start with actions or verbs that solve a smaller problem. We’ll start calling these _functions_:
    
    1  **Pick up** phone book
    2  **Open to** middle of phone book
    3  **Look at** page
    4  If person is on page
    5      **Call** person
    6  Else if person is earlier in book
    7      **Open to** middle of left half of book
    8      Go back to line 3
    9  Else if person is later in book
    10     **Open to** middle of right half of book
    11     Go back to line 3
    12 Else
    13     **Quit**
    
-   We also have branches that lead to different paths, like forks in the road, which we’ll call _conditionals_:
    
    1  Pick up phone book
    2  Open to middle of phone book
    3  Look at page
    4  **If** person is on page
    5      Call person
    6  **Else if** person is earlier in book
    7      Open to middle of left half of book
    8      Go back to line 3
    9  **Else if** person is later in book
    10     Open to middle of right half of book
    11     Go back to line 3
    12 **Else**
    13     Quit
    
-   And the questions that decide where we go are called _Boolean expressions_, which eventually result in answers of yes or no, or true or false:
    
    1  Pick up phone book
    2  Open to middle of phone book
    3  Look at page
    4  If **person is on page**
    5      Call person
    6  Else if **person is earlier in book**
    7      Open to middle of left half of book
    8      Go back to line 3
    9  Else if **person is later in book**
    10     Open to middle of right half of book
    11     Go back to line 3
    12 Else
    13     Quit
    
-   Lastly, we have words that create cycles, where we can repeat parts of our program, called _loops_:
    
    1  Pick up phone book
    2  Open to middle of phone book
    3  Look at page
    4  If person is on page
    5      Call person
    6  Else if person is earlier in book
    7      Open to middle of left half of book
    8      **Go back to line 3**
    9  Else if person is later in book
    10     Open to middle of right half of book
    11     **Go back to line 3**
    12 Else
    13     Quit
    
-   We’ll soon encounter other ideas, too:
    -   functions
        -   arguments, return values
    -   conditionals
    -   Boolean expressions
    -   loops
    -   variables
    -   …
-   And David’s first program just printed “hello, world” to the screen:
    
    ```
    #include <stdio.h>
    
    int main(void)
    {
        printf("hello, world\n");
    }
    ```
    
    -   But this program, written in a language called C, has lots of other syntax that keeps us from focusing on these core ideas.

,< les than
,>