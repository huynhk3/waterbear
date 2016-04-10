# 395 assignment and blog #2
# Khoa Huynh

# April 4, 2016
Been a while since the last update huh (sorry)?

Since the last blog update, I've done some research on why the font-size changing block was not changing the size at all.
Looking at it more closely, I noticed a function that was related to the input section for changing the font size:

[![Waterbear 7](https://github.com/huynhk3/waterbear/blob/master/example7.png)](#features)
======
##### *Figure 1: areas related to the font-size block*

Expanding on this function gives us:

[![Waterbear 8](https://github.com/huynhk3/waterbear/blob/master/example8.png)](#features)
======
##### *Figure 2: Font-size block's javascript function*

After finally isolating where the function is, I looked up the documentation at: http://www.w3schools.com/tags/ref_canvas.asp
and http://www.w3schools.com/tags/canvas_font.asp (this one specifically is related to the font problem). Comparing Waterbear's
javascript to the documentation, it seems as the code is written correctly and shouldn't cause any problems. The user's input
is collected through the box's input box, and saved in the variable "size" as seen in figure 2's function. So what is the problem?

Running an online application to test the code, I found these results:

[![Waterbear 10](https://github.com/huynhk3/waterbear/blob/master/example10.png)](#features)
======
##### *Figure 3: Online testing with hard-coding*

[![Waterbear 11](https://github.com/huynhk3/waterbear/blob/master/example11.png)](#features)
======
##### *Figure 4: Online testing without hard-coding*

Hard coding the values changes the size of the font, but using a variable like how Waterbear handles their function doesn't
change the font at all! Was the size variable not passing the value correctly? Well, looking at figure 4, you can see I used 
window.alert(size[0] + size[1]) to debug, and oddly enough, the value was properly passed! So what's going on here? Find out in
the next blog! (maybe)

# April 9, 2016
Quick and successful update coming up! As of this blog update, the font size mystery has been solved and is working properly!

I've updated the issue on Waterbear's github as well: https://github.com/waterbearlang/waterbear/issues/1324

So, what was the problem? Well at first, I thought the size parameter and sizeString variables were either not returning whatever
was intended, so I had used an alert window pop up with the size variables, and suprisingly the values were correct. What actually
was the problem was 'fontStyle' in the parameters of setFont. For whatever reason (didn't bother doing research on why it was doing
it), it was returning an integer of 2. To fix this, I found a method to collect the user's text input, save it into a new variable
and replace fontStyle. 

[![Waterbear 13](https://github.com/huynhk3/waterbear/blob/master/example13.png)](#features)
##### *Figure 5: IDs related to their respective objects*

#### Before:

[![Waterbear 8](https://github.com/huynhk3/waterbear/blob/master/example8.png)](#features)

#### After:

[![Waterbear 14](https://github.com/huynhk3/waterbear/blob/master/example14.png)](#features)


In the part:

        var family = document.getElementById("familyText").value;

the text in which the user inputs would be saved into 'family', and is grabbed from the HTML with document.getElementById as seen in Figure 5. The ID, "familyText",
had to be added inside the HTML tag so that it may be called and grab the input to be saved.


Now, in case you didn't notice, there is another bug that needed to be fixed as well. For the font block that is used for changing
sizes and font face, there is a selection list for size formatting (px, em, %, pt), and none of them work properly (as in not at all).
For this to be fixed, I had to use the method in the code:

        var list = document.getElementById("fontSizeList").selectedIndex;

where it grabs the ID from the HTML similar to what was used for font families, returns which option in the selection list was 
selected, and saves it into 'list'. The index of the selected option would be called in the if statements and print out the proper size
configuration.

After all that, it finally works properly! Yay! Maybe I'll do a pull request...
