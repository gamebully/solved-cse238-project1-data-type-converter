Download Link: https://assignmentchef.com/product/solved-cse238-project1-data-type-converter
<br>
The purpose of this assignment is to become more familiar with bit-level representations of integers and floating point numbers.

In this project, you will implement an application, in C or Java programming language; that takes

<ul>

 <li>a file containing signed integers, unsigned integers and floating point numbers</li>

 <li>the byte ordering type (Little Endian or Big Endian),</li>

 <li>the size of the floating point data type (the size of both signed and unsigned integers are 2 bytes), as input and converts the contents of the file to hexadecimal according to the predefined format and gives the converted data as output.</li>

</ul>

The size of the data type can be 1, 2, 3, or 4 bytes.

<ul>

 <li>The signed integers are written as normal integers in the file. (e.g., 3, -5, etc.)</li>

 <li>The unsigned integers are written as integers followed by the letter u. (e.g., 3u, 5u, etc.)</li>

 <li>The floating point numbers are written with a decimal point. (e.g., 3.0, 5.987, etc.)</li>

 <li>If the read data type is signed integer, your program will convert the numbers in the input file using 2’s complement representation.</li>

 <li>If the read data type is unsigned integer, numbers will be converted using unsigned integer representation.</li>

 <li>If the read type is floating point number, you will use IEEE-like format. The number of exponent bits according to given data size will be like the following:

  <ul>

   <li>if 1 byte (i.e., 8 bits), 4 bits will be used for exponent part o if 2 bytes (i.e., 16 bits), 6 bits will be used for exponent part o if 3 bytes (i.e., 24 bits), 8 bits will be used for exponent part oif 4 bytes (i.e., 32 bits), 10 bits will be used for exponent part</li>

   <li>While calculating the mantissa to get the floating point value, you will only use the first 13 bits of the fraction part (for 3-byte and 4-byte data sizes). You will use “round to nearest even” method for rounding fraction bits to 13 bits.</li>

  </ul></li>

</ul>

Details about the program are listed below:

<ul>

 <li>At the beginning of the execution, your program will prompt for the input file.</li>

 <li>In the input file, each line will include a single number. <strong><u>Example: input.txt</u></strong></li>

</ul>

29.109375

4u

-9

6u

0

-63.0




<ul>

 <li>After a valid input file is taken as input, the user will be prompted for the byte ordering type and size:</li>

</ul>

<strong>Example: </strong>

Byte ordering: Little Endian

Floating point size: 2 bytes




<ul>

 <li>You program will calculate the hexadecimal value of the file content with the given information:</li>

</ul>

<strong>Example: </strong>

The byte ordering is Little Endian, and the floating point is 2 byte.

<ul>

 <li>First, your program will read the first number of the file. For our “input.txt” the first number is:</li>

</ul>

<strong>29.109375</strong>

<ul>

 <li>This is a floating point number.</li>

</ul>

<strong>29.109375 = 11101.000111 = 1.1101000111 * 2<sup>4</sup></strong>

<ul>

 <li>Mantissa is <strong>1101000111</strong>. However, for 2 bytes, we have 9 bits of fraction part, so we need to round to nearest even: <strong>1.1101000111 </strong><strong>≈ 1.110100100</strong>. The fraction part is <strong>110100100</strong></li>

 <li>E = 4. Exponent is E = exp – Bias, where Bias = 2<sup>6-1</sup> – 1 = 31. Therefore the equation is 4 = exp – 31. exp = 35 which is <strong>100011</strong> in binary.</li>

 <li>The number is positive, so sign bit is 0. <strong>o</strong> The number at total is <strong>0100011110100100</strong> which is <strong>0x47A4</strong> in hexadecimal.</li>

 <li>The byte ordering is Little Endian, so the floating point number is represented as:</li>

</ul>

<strong>A4 47</strong>

<strong> </strong>In the output file, the printed value will be: <strong>A4 47</strong> <strong>Example 2:</strong>

<ul>

 <li>If the program reads the following number, it is:</li>

</ul>

<strong>4u</strong>

<ul>

 <li>This is an unsigned integer. Unsigned integers are 2 bytes:</li>

</ul>

<strong>4 = 0000000000000100</strong>

<ul>

 <li><strong>0000000000000100</strong> is <strong>0x0004</strong> in hexadecimal.</li>

 <li>The byte ordering is Little Endian, so the unsigned integer is represented as:</li>

</ul>

<strong>        04 00</strong>

In the output file, the printed value will be: <strong>04 00</strong> <strong> </strong>

<ul>

 <li>The output file will be:</li>

</ul>

<strong><u>output.txt</u></strong>

A4 47

04 00

F7 FF

06 00

00 00  F0 C9