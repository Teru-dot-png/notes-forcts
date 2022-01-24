## [Mario](https://cs50.harvard.edu/x/2022/notes/1/#mario)

-   Let’s try to print out some blocks to the screen, like those from the video game [Super Mario Bros](https://en.wikipedia.org/wiki/Super_Mario_Bros.). We’ll start with printing four question marks, simulating blocks:
    
    ```
    #include <stdio.h>
    
    int main(void)
    {
        printf("????\n");
    }
    ```
    
-   With a for loop, we can print any number of question marks with better design:
    
    ```
    #include <stdio.h>
    
    int main(void)
    {
        for (int i = 0; i < 4; i++)
        {
            printf("?");
        }
        printf("\n");
    }
    ```
    
    -   After our for loop, we can print a new line. Then we can compile and run our program:
        
        ```
        $ make mario
        $ ./mario
        ????
        $
        ```
        
-   Let’s get a positive integer from the user, and print out that number of question marks, by using a **do while** loop:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        int n;
        do
        {
            n = get_int("Width: ");
        }
        while (n < 1);
    
        for (int i = 0; i < n; i++)
        {
            printf("?");
        }
        printf("\n");
    }
    ```
    
    -   A do while loop does something first, and _then_ checks whether the condition is true. If the condition is still true, then it repeats itself. Here, we’re declaring an integer `n` without specifying a value. Then, we ask the user, with `get_int`, what the value of `n` should be. Finally, we repeat and ask the user for another input only if `n < 1`, since we want to print at least one question mark.
    -   We’ll also change our for loop to use `n` as the number of times we print the question marks.
    -   We can compile and run our program:
        
        ```
        $ make mario
        $ ./mario
        Width: 4
        ????
        $ ./mario
        Width: 40
        ????????????????????????????????????????
        $
        ```
        
-   And we can print a two-dimensional set of blocks with nested loops, or loops one inside the other:
    
    ```
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        int n;
        do
        {
            n = get_int("Size: ");
        }
        while (n < 1);
    
        // For each row
        for (int i = 0; i < n; i++)
        {
            // For each column
            for (int j = 0; j < n; j++)
            {
                // Print a brick
                printf("#");
            }
    
            // Move to next row
            printf("\n");
        }   
    }
    ```
    
    -   We have two nested loops, where the outer loop uses `i` to do some set of things `n` times. The inner loop uses `j` (another conventional variable for counting), a different variable, to do something `n` times for _each_ of those times. In other words, the outer loop prints 3 rows, ending each of them with a new line, and the inner loop prints 3 bricks, or `#` characters, for each line:
        
        ```
        $ make mario
        $ ./mario
        Size: 3
        ###
        ###
        ###
        $
        ```
        
-   We can stop a loop early as well. Instead of the do while loop from earlier, we can use a while loop:
    
    ```
    while (true)
    {
        n = get_int("Size: ");
        if (n > 1)
        {
            break;
        }
    }
    ```
    
    -   With `break`, we can break out of the while loop, which would otherwise repeat forever.