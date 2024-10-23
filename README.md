java c 
P2: RLE with Images Python 
 
Overview 
 
In this project students will develop routines to encode and decode data for images using run-length encoding 
(RLE). Students will implement encoding and decoding of raw data, conversion between data and strings, and 
display of information by creating procedures that can be called from within their programs and externally. This 
project will give students practice with loops, strings, Python lists, methods, and type-casting. 
 
Run-Length Encoding 
 
RLE is a form of lossless compression used in many industry applications, including imaging. It is intended to 
take advantage of datasets where elements (such as bytes or characters) are repeated several times in a row in 
certain types of data (such as pixel art in games). Black pixels often appear in long “runs” in some animation 
frames; instead of representing each black pixel individually, the color is recorded once, following by the number 
of instances. 
 
For example, consider the first row of pixels from the pixel image of a gator 
(shown in Figure 1). The color black is “0”, and green is “2”: 
 
Flat (unencoded) data: 0 0 2 2 2 0 0 0 0 0 0 2 2 0_ 
 
Run-length encoded data: 2 0 3 2 6 0 2 2 1 0_. 
Figure 1 – Gator Pixel Image 
 
The encoding for the entire image in RLE (in hexadecimal) – width, height, and pixels - is: 
 
 
1E|162032602220121F10721AF21092301210326032308250 
 
\W/ \H/ \------------------------------------------PIXELS-----------------------------------------------/ 
 
Image Formatting 
 
The images are stored in uncompressed / unencoded format natively. In addition, there are a few other rules to 
make the project more tractable: 
 
 1. Images are stored as a list of numbers, with the first two numbers holding image width and height. 
 
 2. Pixels will be represented by a number between 0 and 15 (representing 16 unique colors). 
3. No run may be longer than 15 pixels; if any pixel runs longer, it should be broken into a new run. 
 
For example, the chubby smiley image (Figure 2) would contain the data shown in Figure 3. 
 
Figure 2 Figure 3 – Data for “Chubby Smiley” 
 
NOTE: Students do not need to work with the image file format itself – they only need to work with lists and 
encode or decode them. Information about image formatting is to provide context. Requirements 
 
Student programs must present a menu when run in standalone mode and must also implement several methods, 
defined below, during this assignment. 
 
Standalone Mode (Menu) 
 
When run as the program driver via the main() method, the program should: 
 
1) Display welcome message 
 
 2) Display color test (ConsoleGfx.test_rainbow) 
3) Display the menu 
4) Prompt for input 
 
Note: for colors to properly display, it is highly recommended that student 
install the “CS1” theme on the project page. 
 
 
There are five ways to load data into the program that should be provided and four ways the program must be 
able to display data to the user. 
 
Loading a File 
 
Accepts a filename from the user and invokes ConsoleGfx.load_file(filename): 
 
Select a Menu Option: 1 
 
Enter name of file to load: testfiles/uga.gfx 
 
Loading the Test Image 
 
Loads ConsoleGfx.test_image: 
Select a Menu Option: 2_ 
Test image data loaded._ 
 
Reading RLE String 
Reads RLE data from the user in hexadecimal notation with delimiters (smiley example): 
 
Select a Menu Option: 3 
 
Enter an RLE string to be decoded: 28:10:6B:10:10B:10:2B:10:12B:10:2B:10:5B:20:11B:10:6B:10 
 
Reading RLE Hex String 
Reads RLE data from the user in hexadecimal notation without delimiters (smiley example): 
 
Select a Menu Option: 4 
 
Enter the hex string holding RLE data: 28106B10AB102B10CB102B105B20BB106B10 
 
Reading Flat Data Hex String 
Reads raw (flat) data from the user in hexadecimal notation (smiley example): 
 
Select a Menu Option: 5 
 
Enter the hex string holding flat data: 
 
880bbbbbb0bbbbbbbbbb0bb0bbbbbbbbbbbb0bb0bbbbb00bbbbbbbbbbb0bbbbbb0 
 
Displaying the Image 
 
Displays the current image by invoking the ConsoleGfx.display_image(image_data) method. 
 
Displaying the RLE String 
 
Converts the current data into a human-readable RLE representation (with delimiters): 
 
Select a Menu Option: 7 RLE representation: 28:10:6b:10:10b:10:2b:10:12b:10:2b:10:5b:20:11b:10:6b:10 
 
Note that each entry is 2-3 characters; the length is always in dec代 写COP3502、Python
代做程序编程语言imal, and the value in 
hexadecimal! Displaying the RLE Hex Data 
 
Converts the current data into RLE hexadecimal representation (without delimiters): 
 
Select a Menu Option: 8 
 
RLE hex values: 28106b10ab102b10cb102b105b20bb106b10 
 
Displaying the Flat Hex Data 
Displays the current raw (flat) data in hexadecimal representation (without delimiters): 
 
Select a Menu Option: 9 
 
Flat hex values: 880bbbbbb0bbbbbbbbbb0bb0bbbbbbbbbbbb0bb0bbbbb00bbbbbbbbbbb0bbbbbb0 
 
Class Methods 
 
Student classes are required to provide all of the following methods with defined behaviors. We recommend 
completing them in the following order: 
 
1. to_hex_string(data) 
Translates data (RLE or raw) a hexadecimal string (without delimiters). This method can also aid debugging. 
 
Ex: to_hex_string([3, 15, 6, 4]) yields string "3f64". 
 
2. count_runs(flat_data) 
Returns number of runs of data in an image data set; double this result for length of encoded (RLE) list. 
 
Ex: count_runs([15, 15, 15, 4, 4, 4, 4, 4, 4]) yields integer 2. 
 
3. encode_rle(flat_data) 
Returns encoding (in RLE) of the raw data passed in; used to generate RLE representation of a data. 
 
Ex: encode_rle([15, 15, 15, 4, 4, 4, 4, 4, 4]) yields list [3, 15, 6, 4]. 
 
4. get_decoded_length(rle_data) 
Returns decompressed size RLE data; used to generate flat data from RLE encoding. (Counterpart to #2) 
 
Ex: get_decoded_length([3, 15, 6, 4]) yields integer 9. 
 
5. decode_rle(rle_data) 
Returns the decoded data set from RLE encoded data. This decompresses RLE data for use. (Inverse of #3) 
 
Ex: decode_rle([3, 15, 6, 4]) yields list [15, 15, 15, 4, 4, 4, 4, 4, 4]. 
 
6. string_to_data(data_string) 
 
Translates a string in hexadecimal format into byte data (can be raw or RLE). (Inverse of #1) 
 
Ex: string_to_data ("3f64") yields list [3, 15, 6, 4]. 
 
7. to_rle_string(rle_data) 
 
Translates RLE data into a human-readable representation. For each run, in order, it should display the run 
length in decimal (1-2 digits); the run value in hexadecimal (1 digit); and a delimiter, ‘:’, between runs. (See 
examples in standalone section.) 
 
Ex: to_rle_string([15, 15, 6, 4]) yields string "15f:64". 
 
8. string_to_rle(rle_string) 
Translates a string in human-readable RLE format (with delimiters) into RLE byte data. (Inverse of #7) 
 
Ex: string_to_rle("15f:64") yields list [15, 15, 6, 4]. Submissions 
 
NOTE: Your output must match the example output *exactly*. If it does not, you will not receive full credit for 
your submission! 
 
File: 
Method: 
 
 
rle_program.py 
 
Submit on ZyLabs 
 
Do not submit any other files! 
 
Part A (5 points) 
 
For part A of this assignment, students will set up the standalone menu alongside the 4 requirements listed on 
page 2 of this document. In addition to this, students should also set up menu options 1 (loading an image), 2 
(loading specifically the test image), and 6 (displaying whatever image was loaded) in order to help grasp the 
bigger picture of the project. 
 
This involves correctly setting up the console_gfx.py file and utilizing its methods. You will use 
ConsoleGfx.display_image(...) to display images. Notice how it takes in a decoded list. This is the 
 
format in which you will locally (in your program) store any image data that you are working with. When 
the document mentions that something is “loaded” it means that something is stored as a list of flat 
(decoded) data. 
 
Part B (60 points) 
 
For part B of this assignment, students will complete the first 6 methods on page 3 of this document. They 
must match specifications and pass test cases on chapter 12.2 in Zybooks, which will be your means of 
submission for this part of the assignment. Your grade will be the score received on Zybooks. To guarantee 
functionality moving forward to part C, it is expected that you will receive full marks for this section. 
 
Part C (35 points) 
 
For part C of this assignment, students will now complete the final 2 methods on page 3 of this document as well 
as the remainder of the project involving the menu options and understanding how all the individual methods are 
intertwined with each other. You will submit your whole program including the 8 methods listed above and the 
main method in chapter 12.3 in Zybooks. We will only test your remaining 2 methods and the main method in 
part C. 

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
