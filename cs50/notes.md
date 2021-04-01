### Week 0
Scratch introduction
Binaries, computation

### Week 1
#### Introduction to C

arguments are the inputs to functions
functions could have side effects and return values

get_string is not valid c function it was introduced in CS50 course
```C
string answer = get_string("What's your name? ");

printf("hello, %s", answer);
```

to cast variable to another one use syntax:
```C
int x = get_int("")
(float) x
```

##### Data Types

int - integer 32 bits ~ 2^31 - 2^31
`unsigned int ~ 0 - 2^64`  unsigned is a qualifier that allows for certain types to be seen as only postives which moves the range to 2^64

char - single characters

float - decimal 32 bits of precision

double - decimal 64 bits of precision

void - is a tape but not a data type if function returns void it means it does not returns value, it's like placeholder

provided by CS50 <cs50.h>
bool - true or false

string - collection of characters

---
##### Operators
Arithmetic
= - assign
+ - plus
- - minus
/ - divider
% - modulo

Boolean
**every non zero** is true
**zero** is false

&& - AND
|| - OR
! - NOT
< - less then
\> - more then
\<= - less or equal
\>= - more or equal
== - equal
!= - not equal

---
##### Conditions
```C
if (x < y)
{
  // do something
}
else if (x > y)
{
  // do something
}
else
{
  // do something
}

if ()
{}
if ()
{}
if ()
{}
else // binded only with the last if
{}

switch(x)
{
  case 1:
    //do something;
    break; // can be omitted to fall through cases
  case 2:
    //do something;
    break;
  default:
    //do something;
}

int x = (expr) ? 5 : 6; // ternary
```

Chars are single characters and need to be quoted in single quotes ''

##### Loops

```C
while (true)
{
  //do something if condition is true
}

do
{
  // do something at least once and then repeat if condition is true
}
while (true);

int 1 = 0;
while (i < 50)
{
  // do something
  i++;
}

for (int i = 0; i < 50; i++)
{
  // do something
}
```

##### Functions

```C
void my_func(void); //prototype informs compiler that function is declared somewhere else
int main(void)
{
  my_func();
}

void my_func(int n) // void - no args; int n - one argument integer
{
  // do something with n
}

int my_other_func(void) // this function returns integer
{
  int n;
  n = get_int("Integer")
  // do something with n
  return n;
}
```

`dbug50`


#### Array
```C
int scores[3]; // Total number of items in array
scores[0] = 72; // Array have to start with '0' Dahhh ;P
scores[1] = 73;
scores[2] = 33;
```

Constance declaration
cons int TOTAL = 3;

show exit status of program `echo $?`

To pass array to function make:
```C
(void) my_function(int collection[]);
```

You can't return array from function but you can make array static and return
pointer (some more advance C concept)

Command line arguments in C scripts
```C
int main(int argc, string argv[])
{}
```
 - argc, argv - conventional names for command line arguments
  - argc - how much arguments user provided with program name
  - argv - argument vector(array) argv[0] - always the name of the program

