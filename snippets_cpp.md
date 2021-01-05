# outline
- [libraries](#libraries)
- [imports](#imports)

# terminology
- declare: write the variable name and type `int x;`
- initialized: give variable a value `x=5;`

# typedef
assign name to a type (can save space and prevent errors)
`
typedef unordered_map<string, string> coder;
`

# std standard library
`
#include <bitset>
#include <regex>
#include <sstream> // for string manipulation
#include <random>
`

# libraries
`
#include <iostream>
#include <vector> // vector
#include <string> // can use cin, getline
#include <ctime> // for rand()
using namespace std;
`

## iostream
- includes ios, ostream
- enables cin, cout, cerr (for errors), and clog

# compile
single file
`
gcc file.cpp
`

## run single file
`
./file arg1 arg2
`

# imports
`
#include "my_file.h" // file in directory
`

# header file
for library imports and anything necessary to run filename.cpp
`
[main.h]
#include <stdio.h>
`
usually have #ifndef block (called guard)
- must #include filename.h in filename.c 

- can also just declare function before use
`
int func(int x);
int main() {};
int func(int x) { actual code };
`

# error handling
`
throw 1 // error code
`

# debugging error checklist
1. lines end with ;
2. use std:: for string and vector OR add using namespace std;
3. close brackets
4. initialize / declare variable with type
5. look at build log for spelling typos
6. did you return an actual value of the type you specified?
7. check project file structure. if put header/source in subfolder (RELATIVE to the file you're writing in), need to access is using #include "subfolder/file.hpp"

## assert
- will stop execution if false and print which statement failed
`
assert(a==b)
`

# inline
- can speed up run time but add code space
`
inline int min(int a, int b) {return a<b?a:b}
`

# command line arguments
`
int main(int argc, char** argv[]) { // argc is how many params were passed, argv are the actual arguments
	.
}
`

# macros
- piece of code that is replaced by the value of the macro
`
define AREA(len, wid) (len * wid)
`

# constants
- define and const similar enough

## define
` [before main]
#define MY_CONSTANT 7
#define PROGNAME "my_compressor"
`

## const
`
[before main] const MYNUM = 9;
`

## ifndef (IF NOT DEFINED)
checks for defined constant
`
#ifndef DEFAULT_OPTION
#define DEFAULT_OPTION 4
#endif
`

## ifdef (IF DEFINED)
`
#ifdef DEFAULT_OPTION
#define DEFAULT_OPTION 4
#else
// code
#endif
`

# vector
`
#include <vector>
vector<int> list; // or vector<int> list(5);
list.size(); // length
list.push_back(val); // append
list.pop_back(); // remove last item
`

# file stream
`
#include <fstream>
fstream input;
input.open("my_file.txt", ios::in);
or
ifstream input("my_file.txt"); // input-fstream
or
file = fopen("my_file.txt", "rb");
`
**be sure to close files**
`
file.close();
`

## check if open
`
if(a_file.isopen()) break;
`

## read string from file
`
char str[10]; // list of 10 chars?
b_file >> str;
`

## set file position
`
fseek(file, 0, 0); // stream, offset, origin params
`

## end of file
`
if(feof(fstream_object)) printf("end of file")
`

## write to file
`
ret = fwrite(1, 2); // returns errors and if none returns position?
`
better way:
`
outfile << "this line will be written to you!";
`

# operators

## ternary
- like consice if/else
`
int c = (5 > 2) ? 1 : 0
`

# memset
`
memset(pointer_of_mem_block, value, num_bytes)
`
`
char str[] = "almost there";
memset (str, '-', 6);
puts (str); // prints "------ there"
`

# calloc
- takes in number_of_objects and size_of_objects
- sets bits to 0
`
calloc(size, sizeofeach)
`

# malloc
- allocates memory to be initialized later
- nullptr if memory allocation fails or if 0 bytes
`
void* malloc(30); // bytes
`

# data types

## NULL

## auto
- cpp infers type
`
auto x = 5; // int
`

## int
- at least 16 bits
- long at least 32
- short at least 16

## char
`
char h='a' // convention to use single-quote for char
`
- unsigned can hold 8 bits per symbol

## FILE
`
FILE *file;
`

## 

## print contents
`
string text;
input >> text;
while(getline(input, text)) {
	cout << text << endl;
}
input.close();
`

## write out
`
ofstream file("output.txt")
file << "hello";
`

# matrix
`
#include "m\matrix.h"
matrix<int> m(3, 4, 0);
`

# strings
`
#include <string>
s.length();
s.resize(int);
s.at(index);
s + "s"; // concatenate
s.substr(start, length);
s.find(substring);
s.find_first_of(substring, start_index);
`

can also define a string with char
`
const char* str = "hello world!";
`

# struct
`
struct Yeti {
	string name;
}; // must end with semi-colon
Yeti y1("jeff");
`
can put starter object names after curly to use them later
`
struct Yeti {
	string name;
} bigfoot;
[in main] bigfoot.name = "hello";
`

## bit field
`
struct S {
	unsigned int b : 3; // any number 0-7
}
[in main] S s = {6};
++s.b; // now 7 is stored in the bit field
`

# typecasting conversion
`
double five_halves = 2.5;
cout << (int)(five_halves); // 2
`

# templates
`
template <class T>
T sum (T a, T b) {
	T result;
	result = a + b;
	return result;
}
[in main] int i=5, j=6, k;
double f=2.0, g=0.5, h;
k=sum<int>(i, j);
h = sum<double>(f, g);
`
in above, T holds the type of return type and input type. calling it in main eg `sum<int>` tells template to use type int for T.


# pointers / dereference operator (`*`)
`*thing` read as "value pointed to by thing"

`
a->b;
or
(*a).b;
`

`
char* x;
or
char *x;
`
- if you want to access `int x[]={5,6}`'s value when passing to function, make function ?? 

## double pointer
`
int **x;
`

# address-of-operation (&) reference
`&thing` read as "address of thing"
`
myvar = 25;
foo = &myvar; // address of myvar, eg 1776
bar = myvar; // value of myvar, 25
`
passing by reference means using the actual thing




# classes
private - only accessible from members of same class
public - accessible anywhere where object is visible

`
class Rectangle {
	int width; height;
	public:
		void set_values(int, int);
		int area() {
			return width*height
}; // REMEMBER semi-colon
void Rectangle::set_values(int x, int y) { // set_values only in namespace of Rectangle but use :: since not inside class
	width = x;
	height = y;
}
[in main] Recangle rect;
rect.set_values(3, 4);
cout << rect.area();
`

## create new object
`
Myclass *object = new Myclass();
`
or
`
Myclass myclass(12);
`


## self-reference
`
this.method() // must use this keyword, similar to self
`


# enum
`
 enum class Colors {black, green, blue};
Colors mycolor;
mycolor = Colors::blue;
`

`
enum class Eyecolor : char {blue, green, brown};
`
# type (get type)
`
#include <typeinfo>
cout << typeid(k).name();
`

# arrays
`
int list[5];
list[1] = 7;
int len = sizeof(arr) / sizeof(arr[0]); 
`

# list
# deque
# set
# map

# time
`
clock() // time since program started
time() // time since epoch
`

## sleep
`
#include <unistd.h>
sleep(SLEEP_LENGTH); // seconds
`

# random
`
#include <ctime>
[in main] srand(time(0));
rand()
`

# functions and parameters
`
`

# escape
`
\a 	// windows sound
\0 	// null character. useful to put at end of array and check for it in while condition
\n  // newline
\t  // tab
`

# printing
cout and printf pretty similar for most purposes
`
cout << "hello" << endl;
`
or 
`
printf("hello %d %s", id, message);
`

## print string
`
puts (string); // prints '\n' at the end
`

# switch
`
switch(var) {
	case 1:
		break;
	case 3:
		break;
	default:
		break;
}
`

#  binary bitwise operators
`
|= // OR
~ // NOT
`

# data structures

## queue
`
#include <queue>
priority_queue<object> pq;
pq.push(ele); // append
pq.top(); // first item
pq.pop();  // removes top item and returns others;
pq.size() // length
`

## unordered map
`
#include <unordered_map>
unordered_map<char, string> huffman;
huffman['a'] = "hello";
for (auto x : huffman) 
  cout << x.first << " " << x.second << endl; 
huffman.erase('a');
cout << huffman.size(); // length
 `
`