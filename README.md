Download Link: https://assignmentchef.com/product/solved-csci251-csci851-assignment-3-code-book-container
<br>
This assignment involves implementing container and class functionality to support measuring the properties of certain classes of codes.

<h1>General notes</h1>

These are some general rules about what you should and shouldn’t do.

<ol>

 <li>Your assignment should be sensibly organised with the same kind of expectations in this area as theprevious assignments. No memory leaks etc. too.</li>

 <li>Your code must compile on Banshee with the compilation instructions you provide in txt. If it doesn’t you will likely receive zero for the coding part of the assignment. Note that you will have to use -std=c++11 for the inclusion to work correctly.</li>

 <li><strong>Other than the initial command line input, the program should run without user input.</strong></li>

 <li>You should use classes.</li>

 <li>You should use templating.</li>

 <li>You shouldn’t use inheritance.</li>

 <li>Failure to comply with any of the three points above will result in significant penalties.</li>

</ol>

<h1>Some coding (theory) containers</h1>

You are to implement two containers:

<ol>

 <li>A Codeword container for storing ordered lists of symbols making up a codeword.</li>

 <li>A Codebook container containing a collection of codewords.</li>

</ol>

The symbols are themselves allowed to be of any type that supports certain functionality. We shall consider the containers after considering the two symbol classes you need to implement.

<h2>The symbol classes</h2>

Note that you should not relate these classes by inheritance. Each instance of these classes stores a single value.

<ol>

 <li>The first symbol class Mint allows us to store a single integer value in the range 0 to <em>p</em>−1, where p is a positive integer, the modulus. In this class you should overload the subtraction operator overloaded to produce the typical integer result modulo p.</li>

 <li>The second symbol class Melt allows us to store a single lowercase letter from the English alphabet, with the subtraction operator overloaded to give 1 if the symbols are different and 0 if they are the same. There are <em>p </em>= 26 distinct possible symbols.</li>

</ol>

See later for a description of the main() function. Both should also have a special ”zero” symbol, for Mint this will be the integer 0, while for Melt it will be a letter ’a’.

<h2>The Codeword container</h2>

This container should be used to store elements of the same type. It should be a templated container class. The following methods should also be provided.

<ol>

 <li>The method Weight should determine the number of elements in the code that are not–equal to the ”zero” symbol. For example, 0 2 0 3 3 3 0 has a weight of 4.</li>

 <li>The method Distance should take another codeword and determine the sum of the element by element difference according to the overloaded subtraction operation for the contained symbol class.</li>

</ol>

For example, the distance between 0 1 2 3 0 1 and 0 0 2 0 0 2 for a Mint container with <em>p </em>= 7 would be determined as

0 1 2 3 0 1 – 0 0 2 0 0 2

————–

0+1+0+3+0+6 = 10

<ol start="3">

 <li>The method Display should output the elements in the codeword, each separated by a space, with a final gap and the weight of the codeword displayed. For example,</li>

</ol>

4 6 9 11 3              Weight: 5

<h2>The Codebook container</h2>

This container should be used to store collections of codewords. It should be a templated container class. The following methods should be provided.

<ol>

 <li>The method minimumWeight should determine the minimum Weight value across all non–zero codewords.</li>

 <li>The method calcDistance should determine the distances between every pair of codewords in the code, and store these values.</li>

 <li>The method minimumDistance should determine the minimum Distance between two codewords in the code, as determined across all distinct pairs of codewords.</li>

 <li>The method Display should display all the codewords contained in the container, using the Display method for the codewords themselves, and display the minimum weight and minimum distance for this code. The table of distances between codewords should be displayed also.</li>

</ol>

This container should contain a zero codeword, with the elements being all ”zero”, in accordance with the zero element for the contained symbol class.

<h2>Containers for Codes: The main() function</h2>

Once your program is compiled into the executable CFC it must run as follows:

./CFC 0 seed length size modulus

./CFC 1 seed length size where the parameters have the following meanings:

<ul>

 <li>First argument : (0 for Mint, 1 for Melt).</li>

 <li>seed : A positive integer. Random seed for use in the value generator functions.</li>

 <li>length : A positive integer. The number of symbols in each codeword. • size : A positive integer. The number of codewords in each codebook.</li>

 <li>modulus : A positive integer, only relevant for the Mint</li>

</ul>

You generate values to populate your codewords by making calls to the functions provided in generateValue.h and libGenVal.a, using seed and modulus as arguments as needed.

After populating the codebook, you should calculate the minimum weights and distances for the code.

The code should be displayed using the code method Display().

<h2>Some test data</h2>

Here goes a couple of test data cases. These are the actual codebooks, including the the zero codewords. See also some examples in the Week 11 lecture/tutorial.

$ ./CFC 0 100 5 4 23

0 0 0 0 0

12 15 6 9 9

12 19 3 0 3

2 4 15 4 18

$ ./CFC 1 101 5 4 a a a a a n o o y a z e a r n v h h p x