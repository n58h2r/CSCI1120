java cCSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
Assignment 2: Gumball Machines
Due: 23:59, Thu 3 Oct 2024 File name: gumball.cpp Full marks: 100
Introduction
The objective of this assignment is to let you practice control flow structures in C++. It also involves the use of variables, operators, expressions, and standard input/output to reinforce your learning in the course thus far. You are to write a program to print an ASCII character pattern resembling the drawing of a gumball vending machine, such as Figure 1 below.
     container
_____ /____\ // \\ // \\ // OOOOO\\ //OOOOOOO\\ \\OOOOOOO// \\OOOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| |
𝑛 = side length of the hexagon gum
gum flap (chute door)
𝑛 = side length of the square
     stand || || |_ _ _ _ _|
Figure 1: A sample character pattern resembling a gumball machine This gumball machine character pattern is composed of two parts:
1. Container: A hexagonal shape in double dashed lines is used to represent the container holding the gumballs. Each gumball is denoted by a capital letter 'O'.
2. Stand: A square shape below the hexagon is used to represent the stand supporting the gumball container. A small square of unit length (always at the center of the 2nd line) inside this stand shape is used to represent the chute door, i.e., the opening where gumballs come out.
The whole pattern is formed from the set of characters in Table 1 below. Table 1: Characters for printing the ASCII art drawing
  Character
Name of the Character
  _ Underscore
| Pipe (Vertical bar)
\ Backslash
/ Forward slash
O Letter O (denoting a gum)
Space Copyright © 2024 CSE, CUHK
Page 1 of 8
            
CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
Instead of hardcoding, you are required to use loops and conditionals to print the drawing whose size can be scaled up or down according to the user input (See Table 2 for examples).
User Input
There are two user inputs required at the program start.
1. Side length (𝑛): it is the side length of the hexagon (or the square). This input controls the number of underscores that form the outer edge of the hexagon.
2. Stock of gumballs (𝑠𝑡𝑜𝑐𝑘): the initial number of gumballs to load into the vending machine.
Due to the double dashed line design of the hexagon and the spaces involved, the maximum number of gumballs that can be put into the container, i.e., its capacity (𝑐), is limited and determined by the following formula (deduced from the sum formula of an arithmetic series):
𝑐 = 3𝑛! − 8𝑛 + 5 ... (1)
Input validation
1. If the side length (𝑛) is smaller than 3, there is not enough room to print the chute door. When 𝑛 is getting too big, the output may overrun your terminal width and look distorted due to line wrapping. So, let us assume its valid range is between 3 and 29. (Note: in case you still see line wrapping issues in this range, you may resize your terminal via its settings.)
2. The initial number gumballs (𝑠𝑡𝑜𝑐𝑘) to load into the machine must lie between ⌊𝑐/2⌋ (floor of the division) and 𝑐, inclusive.
If the user input falls outside the valid range, the program will terminate immediately with an error message. See the Sample Runs section.
Size Scaling
Table 2 shows some examples to explain how the container shape and its capacity (𝑐) scale with the side length (𝑛) input.
Note that for making the width and height of the hexagon (or square) look similar in the console, we put a single space between every two underscores or two letter O’s in a horizontal line. For better visualization of the spaces required to produce the output, we used the symbol ␣ to denote a space character.
Machine Operations
Besides printing the gumball machine, the program will also prompt the user to enter a quantity of gumballs to buy. When the user enters a valid value (between 1 and 𝑠𝑡𝑜𝑐𝑘), the quantity will be deducted from the stock and there will be fewer O’s shown in the next printout of the gumball machine. The program keeps repeating these operations until running out of stock.
 Copyright © 2024 CSE, CUHK Page 2 of 8

CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
Table 2: Sample output versus side length (𝑛) 𝒏3456
𝒄8 21 40 65
         ␣␣␣␣_␣_␣_ ␣␣/␣␣_␣_␣␣\ ␣/␣/␣O␣O␣\␣\ /␣/␣O␣O␣O␣\␣\ \␣\␣O␣O␣O␣/␣/ ␣\␣\␣_␣_␣/␣/ ␣␣\␣_␣_␣_␣/ ␣␣␣|␣␣_␣␣| ␣␣␣|␣|_|␣| ␣␣␣|_␣_␣_|
    ␣␣␣␣␣_␣_␣_␣_ ␣␣␣/␣␣_␣_␣_␣␣\ ␣␣/␣/␣O␣O␣O␣\␣\ ␣/␣/␣O␣O␣O␣O␣\␣\ /␣/␣O␣O␣O␣O␣O␣\␣\ \␣\␣O␣O␣O␣O␣O␣/␣/ ␣\␣\␣O␣O␣O␣O␣/␣/ ␣␣\␣\␣_␣_␣_␣/␣/ ␣␣␣\␣_␣_␣_␣_␣/ ␣␣␣␣|␣␣␣_␣␣␣| ␣␣␣␣|␣␣|_|␣␣| ␣␣␣␣|␣␣␣␣␣␣␣| ␣␣␣␣|_␣_␣_␣_|
   ␣␣␣␣␣␣_␣_␣_␣_␣_ ␣␣␣␣/␣␣_␣_␣_␣_␣␣\ ␣␣␣/␣/␣O␣O␣O␣O␣\␣\ ␣␣/␣/␣O␣O␣O␣O␣O␣\␣\ ␣/␣/␣O␣O␣O␣O␣O␣O␣\␣\ /␣/␣O␣O␣O␣O␣O␣O␣O␣\␣\ \␣\␣O␣O␣O␣O␣O␣O␣O␣/␣/ ␣\␣\␣O␣O␣O␣O␣O␣O␣/␣/ ␣␣\␣\␣O␣O␣O␣O␣O␣/␣/ ␣␣␣\␣\␣_␣_␣_␣_␣/␣/ ␣␣␣␣\␣_␣_␣_␣_␣_␣/ ␣␣␣␣␣|␣␣␣␣_␣␣␣␣| ␣␣␣␣␣|␣␣␣|_|␣␣␣| ␣␣␣␣␣|␣␣␣␣␣␣␣␣␣| ␣␣␣␣␣|␣␣␣␣␣␣␣␣␣| ␣␣␣␣␣|_␣_␣_␣_␣_|
   ␣␣␣␣␣␣␣_␣_␣_␣_␣_␣_ ␣␣␣␣␣/␣␣_␣_␣_␣_␣_␣␣\ ␣␣␣␣/␣/␣O␣O␣O␣O␣O␣\␣\ ␣␣␣/␣/␣O␣O␣O␣O␣O␣O␣\␣\ ␣␣/␣/␣O␣O␣O␣O␣O␣O␣O␣\␣\ ␣/␣/␣O␣O␣O␣O␣O␣O␣O␣O␣\␣\ /␣/␣O␣O␣O␣O␣O␣O␣O␣O␣O␣\␣\ \␣\␣O␣O␣O␣O␣O␣O␣O␣O␣O␣/␣/ ␣\␣\␣O␣O␣O␣O␣O␣O␣O␣O␣/␣/ ␣␣\␣\␣O␣O␣O␣O␣O␣O␣O␣/␣/ ␣␣␣\␣\␣O␣O␣O␣O␣O␣O␣/␣/ ␣␣␣␣\␣\␣_␣_␣_␣_␣_␣/␣/ ␣␣␣␣␣\␣_␣_␣_␣_␣_␣_␣/ ␣␣␣␣␣␣|␣␣␣␣␣_␣␣␣␣␣| ␣␣␣␣␣␣|␣␣␣␣|_|␣␣␣␣| ␣␣␣␣␣␣|␣␣␣␣␣␣␣␣␣␣␣| ␣␣␣␣␣␣|␣␣␣␣␣␣␣␣␣␣␣| ␣␣␣␣␣␣|␣␣␣␣␣␣␣␣␣␣␣| ␣␣␣␣␣␣|_␣_␣_␣_␣_␣_|
   Program Specification
1. The program first prompts the user for the side length 𝑛.
2. If 𝑛 is invalid (not between 3 and 29), the program prints an error message and terminates.
3. Print the machine capacity 𝑐, given by equation (1).
4. Prompt the user for the 𝑠𝑡𝑜𝑐𝑘 of gumballs.
5. If 𝑠𝑡𝑜𝑐𝑘 is invalid (not between ⌊𝑐/2⌋ and 𝑐), print an error message an代 写CSCI1120、C++
代做程序编程语言d terminate the program.
6. Print the gumball machine using loops and conditionals. This step comprises more subtasks like:
a. Determine the left padding, i.e., how many spaces to print before /, \ or | per row. b. Print the hexagonal part.
c. Align the current stock of gumballs properly inside the container.
d. Print the square part.
7. Prompt the user for the quantity 𝑞 to buy.
8. If 𝑞 is invalid (not between 1 and 𝑠𝑡𝑜𝑐𝑘), print an error message and go back to step 6.
9. Deduct 𝑞 from 𝑠𝑡𝑜𝑐𝑘.
10. If 𝑠𝑡𝑜𝑐𝑘 > 0, go back to step 6.
11. Print the message "Sold out!" finally.
Note two important points:
• (Regarding 6.b) For a hexagon container full of gumballs, the number of gumballs varies by one
when going from one row to the next, except the two rows in the middle of the hexagon.
• (Regarding 6.c) Gumballs are dispensed or “consumed” in a top-to-bottom, left-to-right manner. The gumballs on the top row should be aligned to the right if their count is less than the row’s capacity (see Figure 1 again). Once consumed, the letter 'O' denoting a gumball will be replaced
by a space character.
Assumptions: You can assume that all user inputs are always entered as integers. The program behavior beyond this assumption can be indeterminate and your program behavior can be different from our sample program.
Copyright © 2024 CSE, CUHK Page 3 of 8

CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
Restrictions: You are NOT allowed to use any arrays, vectors, or any other data containers in this assignment. You may use the string class (e.g., to store a line of characters if you see fit) but you cannot use its at() method or the subscript operator [] to traverse the individual characters of a string. Defining your own functions or macros is allowed but not mandatory.
Sample Runs
In the following sample runs, the blue numbers after ':' are user inputs and the other text is the program printout. You can try the provided sample program for other inputs. Your program printout shall be exactly the same as the sample program (same text, symbols, letter case, spacings, etc.). Note that there is a space after the ':' included in each input prompt.
    Enter side length: -1↵ Invalid side length!
Enter side length: 30↵ Invalid side length!
Enter side length: 4↵
Machine capacity: 21
Enter gumball stock: 9↵
Too few / many gumballs to load!
Enter side length: 4↵
Machine capacity: 21
Enter gumball stock: 22↵
Too few / many gumballs to load!
Enter side length: 6↵
Machine capacity: 65
Enter gumball stock: 31↵
Too few / many gumballs to load!
Enter side length: 4↵ Machine capacity: 21 Enter gumball stock: 10↵
____ /___\ // \\ // \\ // O\\ \\OOOOO// \\OOOO// \\___// \____/ |_|
| |_| | ||
|_ _ _ _|
Enter quantity to buy: 1↵ Copyright © 2024 CSE, CUHK
Page 4 of 8
          
CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
____ /___\ // \\ // \\ // \\ \\OOOOO// \\OOOO// \\___// \____/ |_|
| |_| | ||
|_ _ _ _| Enter quantity to ____ /___\ // \\ // \\ // \\ \\ // \\OOOO// \\___// \____/ |_|
| |_| | ||
|_ _ _ _| Enter quantity to Invalid quantity! ____ /___\ // \\ // \\ // \\ \\ // \\OOOO// \\___// \____/ |_|
| |_| | ||
|_ _ _ _| Enter quantity to ____ /___\ // \\ // \\ // \\ \\ // \\ // \\___// \____/ |_|
| |_| | ||
|_ _ _ _|
Sold out!
buy: 5↵
buy: 5↵
buy: 4↵
 Copyright © 2024 CSE, CUHK
Page 5 of 8

CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
 Enter side length: 5↵ Machine capacity: 40 Enter gumball stock: 25↵
_____ /____\ // \\ // \\ // \\ //OOOOOOO\\ \\OOOOOOO// \\OOOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Enter quantity to buy: 26↵ Invalid quantity!
_____ /____\ // \\ // \\ // \\ //OOOOOOO\\ \\OOOOOOO// \\OOOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Enter quantity to buy: 0↵ Invalid quantity!
_____ /____\ // \\ // \\ // \\ //OOOOOOO\\ \\OOOOOOO// \\OOOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Enter quantity to buy: 10↵ Copyright © 2024 CSE, CUHK
Page 6 of 8

CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
_____ /____\ // \\ // \\ // \\ // \\ \\ OOOO// \\OOOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Enter quantity to buy: 5↵ _____
/____\ // \\ // \\ // \\ // \\ \\ // \\ OOOOO// \\OOOOO// \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Enter quantity to buy: 10↵ _____
/____\ // \\ // \\ // \\ // \\ \\ // \\ // \\ // \\____// \_____/ |_|
| |_| | || ||
|_ _ _ _ _|
Sold out!
 Copyright © 2024 CSE, CUHK
Page 7 of 8

CSCI1120 Introduction to Computing Using C++, Fall 2024/25
Department of Computer Science and Engineering, The Chinese University of Hong Kong
Submission and Marking
§ Your program file name shall be gumball.cpp. Submit the file in Blackboard (https://blackboard.cuhk.edu.hk/).
§ Insert your name, student ID, and e-mail as comments at the beginning of your source file. // CSCI1120 Assignment 2
   // Name:
   // Student ID:
   // Email: (the one that you check most often)
§ You can submit your assignment multiple times. Only the latest submission counts.
§ Your program shall be free of compilation errors and warnings when built in VS Community 2022.
§ Your program shall include suitable comments as documentation.
§ Do NOT share your work to others and do NOT plagiarize. Both senders and plagiarists shall be
penalized.
           Copyright © 2024 CSE, CUHK Page 8 of 8

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
