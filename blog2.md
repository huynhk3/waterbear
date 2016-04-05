# 395 assignment and blog #2
# Khoa Huynh

# April 4, 2016
Been a while since the last update huh (sorry)?

Since the last blog update, I've done some research on why the font-size changing block was not changing the size at all.
Looking at it more closely, I noticed a function that was related to the input section for changing the font size:

[![Waterbear 7](https://github.com/huynhk3/waterbear/blob/master/example7.png)](#features)
Figure 1: areas related to the font-size block

Expanding on this function gives us:

[![Waterbear 8](https://github.com/huynhk3/waterbear/blob/master/example8.png)](#features)
Figure 2: Font-size block's javascript function

After finally isolating where the function is, I looked up the documentation at: http://www.w3schools.com/tags/ref_canvas.asp
and http://www.w3schools.com/tags/canvas_font.asp (this one specifically is related to the font problem). Comparing Waterbear's
javascript to the documentation, it seems as the code is written correctly and shouldn't cause any problems. The user's input
is collected through the box's input box, and saved in the variable "size" as seen in figure 2's function. So what is the problem?

Running an online application to test the code, I found these results:

[![Waterbear 10](https://github.com/huynhk3/waterbear/blob/master/example10.png)](#features)
Figure 3: Online testing with hard-coding
======
[![Waterbear 11](https://github.com/huynhk3/waterbear/blob/master/example11.png)](#features)
Figure 4: Online testing without hard-coding

Hard coding the values changes the size of the font, but using a variable like how Waterbear handles their function doesn't
change the font at all! Was the size variable not passing the value correctly? Well, looking at figure 4, you can see I used 
window.alert(size[0] + size[1]) to debug, and oddly enough, the value was properly passed! So what's going on here? Find out in
the next blog! (maybe)