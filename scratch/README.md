# What is Computer Science?

Computer science is fundamentally about problem-solving.

We can think of problem-solving as the process of taking some information (details about our problem) and generating some results (the solution to our problem). The “black box” in the middle is computer science, or the code we’ll learn to write.

To begin doing this, we’ll need a way to represent inputs and outputs so that we can store and work with information in a standardized way.

## Representing Numbers

Let’s start with the task of counting the number of people in a room. Using our hand, we can raise one finger for each person, but we won’t be able to count very high. This system is called unary, where each digit represents a single value of one.

You’re probably familiar with a more efficient system for representing numbers, where we have ten digits, from 0 to 9:

`0 1 2 3 4 5 6 7 8 9`

This system is called decimal, or base 10, since there are ten different values a digit can represent.

Computers use a simpler system called binary, or base two, with only two possible digits, 0 and 1. Each binary digit is also called a bit.

Since computers work with electricity, which can be turned on or off, we can conveniently represent a bit by turning some switch on or off to represent 0 or 1.

Using a light bulb, for example, we can turn it on to count to 1.

With three light bulbs, we can turn them on in different patterns and count from 0 (with all three off) to 7 (with all three on):

Inside modern computers, there aren’t light bulbs, but millions of tiny switches called transistors that can be turned on and off to represent different values. For example, we know that the following number in decimal represents one hundred twenty-three:

`1 2 3`

The 3 is in the ones place, the 2 is in the tens place, and the 1 is in the hundreds place.

So, 123 is `100 × 1 + 10 × 2 + 1 × 3 = 100 + 20 + 3 = 123`.

Each place of a digit represents a power of ten since there are ten possible digits for each place. The rightmost place is for 10⁰, the middle place is for 10¹, and the leftmost place is for 10².

10² 10¹ 10⁰ 1 2 3

In binary, with only two digits, we have powers of two for each place value:
2² 2¹ 2⁰ 4 2 1

With all the switches or light bulbs off, we still have a value of 0:
2² 2¹ 2⁰ 0 0 0

Now, if we change the binary value to, say, 011, the decimal value would be 3 since we sum 2 and 1:
4 2 1 0 1 1

If we had more light bulbs, we could have a binary value of 110010, which would have the equivalent decimal value of 50:
32 16 8 4 2 1 1 1 0 0 1 0


Notice that `32 + 16 + 2 = 50`. With more bits, we can count even higher numbers.

## Text

To represent letters, we need to decide how numbers map to letters. Some people, many years ago, collectively agreed on a standard mapping of numbers to letters. The letter “A,” for example, is number 65, and “B” is 66, and so on. By using context, like when we’re looking at a spreadsheet or an email, different programs can interpret and display the same bits as either numbers or text.

The standard mapping, ASCII, also includes lowercase letters and punctuation.

If we received a text message with a bit pattern that had the decimal values 72, 73, and 33, those bits would be mapped to the letters HI!. Each letter is typically represented with a pattern of eight bits, or one byte, so the bit sequences we would receive are `01001000`, `01001001`, and `00100001`.

We might already be familiar with using bytes as a unit of measurement for data, like in megabytes or gigabytes, for millions or billions of bytes.

With eight bits, or one byte, we can have `2⁸` or 256 different values (including zero). (The highest value we can count to would be 255.)

Other characters, like accented letters and symbols in other languages, are part of a standard called Unicode, which uses more bits than ASCII to accommodate all those characters.

When we receive an emoji, our computer is simply receiving a binary number that maps to the emoji image based on the Unicode standard. For example, the “face with tears of joy” emoji is represented by the bits `000000011111011000000010`:

😂

## Images, Videos, and Sounds

An image, like the emoji image, is made up of colors. With just bits, we can map numbers to colors as well. There are many different systems for representing colors, but one common one is RGB, which represents different colors by indicating the amount of red, green, and blue within each color.

For example, our earlier bit pattern, `72, 73, 33`, could indicate the amount of red, green, and blue in a color. (And our programs would know that those bits map to a color if we opened an image file instead of receiving them in a text message.)

Each number could be a byte, with 256 possible values, so with three bytes, we can represent millions of colors. Our three bytes above would represent a dark shade of yellow:

Notice this example.

The dots, or squares, on our screens are called pixels, and images are made up of thousands or millions of these pixels too. So, using three bytes to represent the color of each pixel, we can create images. We can see the pixels in an emoji if we zoom in, for example:

The resolution of an image is the number of pixels that exist, horizontally and vertically, so a high-resolution image will have more pixels and require more bytes to store.

Videos are made up of many images, changing several times per second to give us the appearance of movement, just like an old flipbook would.

Music can also be represented with bits, mapping numbers to notes and durations, or more complex mappings of bits to sound frequencies at each moment in time.

File formats, like JPEG and PNG, or Word or Excel documents, are also based on some standard that people have agreed on, to represent information with bits.

## Algorithms

Now that we can represent inputs and outputs, we can work on problem-solving.

Humans can also follow algorithms, like recipes for cooking. When programming a computer, we need to be more precise with our algorithms so that our instructions aren’t ambiguous or misinterpreted.

We might have an app on our phones that stores our contacts, with their names and phone numbers sorted alphabetically. The “old-school” equivalent might be a phone book, a printed copy of names and phone numbers.

Our input to the problem of finding someone’s number would be the phone book and a name to look up. We could open the book and start from the first page, looking for a name one page at a time. This algorithm would be correct since we’ll eventually find the name we’re looking for if it’s in the book.

We could flip through the book two pages at a time, but this algorithm wouldn’t be correct because we might skip the page with our name on it. We could fix that bug, or mistake, by flipping back one page if we go too far, since we know the phone book is sorted alphabetically.

Another algorithm would be to open the phone book in the middle, decide whether our name will be in the left half or the right half of the book (because the book is in alphabetical order), and cut the size of our problem in half. We can repeat this until we find our name, cutting the problem in half each time. With 1,024 pages to start, we would only need 10 steps of cutting the book in half before we have just one page left to check. We could see this visualized in an animation of splitting a phone book in half repeatedly, compared to the animation of searching one page at a time.

In fact, we can represent the efficiency of each of these algorithms with a graph:

Our first solution, searching one page at a time, can be represented by the red line: our solving time increases linearly as the problem size increases. `n` is a number representing the problem size, so with `n` pages in our phone books, we have to perform up to `n` steps to find a name.

The second solution, searching two pages at a time, can be represented by the yellow line: our slope is less steep, but still linear. Now we only need (approximately) `n / 2` steps since we turn two pages at a time.

Our final solution, splitting the phone book in half each time, can be represented by the green line, with a fundamentally different relationship between problem size and solving time: logarithmic, as our solving time increases more and more slowly as the problem size increases.

In other words, if the phone book were to go from 1,000 to 2,000 pages, we would only need one more step to find our name with the binary search algorithm. With a billion pages, we would only need to open the book 30 times.

The difference between algorithms might not seem significant for something small, but in computers, where we process huge amounts of information, finding more efficient algorithms makes a huge difference.

## Pseudocode

To describe algorithms, we often write out our instructions with pseudocode, a human-readable way of representing code or logic.

In our phone book example, we might write pseudocode like this:

1. Pick up the phone book.
2. Open to the middle of the phone book.
3. Look at the page.
4. If the name is on the page:
   - Call the person.
5. Otherwise, if the name is earlier in the book:
   - Open to the middle of the left half of the book.
6. Otherwise, if the name is later in the book:
   - Open to the middle of the right half of the book.
7. Repeat until you find the name or give up.

This example also uses conditions to take one of several possible actions. This algorithm doesn’t contain any bugs because we’ll always be able to find the name if it’s in the book. The algorithm also contains a loop that will repeat until the name is found.

## Summary

In summary, computer science encompasses how we represent and process information, from numbers and text to images, video, and sound, all the way to designing efficient algorithms to solve complex problems.
