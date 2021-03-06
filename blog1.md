# 395 assignment and blog #1
# Khoa Huynh

# About me
Many people when they start out programming suffer from a common syndrome called the, "imposter syndrome.� 
This is usually when you feel like you�re out of depth with learning code and creating programs, and doubt your own abilities 
and skills. Honestly, I�ve had this feeling many times throughout my MacEwan studies, but with the help of my instructors I�ve 
regained faith in myself (multiple times) and even made some interesting programs. 
With their continued guidance, I hope to publish proper code and artifacts with not only this assignment, but for future 
endeavors.
 
# What this blog is about
This blog is my interactions and thoughts about the web application Waterbear. Waterbear is a website where users can use it's
visual block syntax to program things in a different manner, and to help others that have different learning methods introduce
themselves to coding. 

# March 5, 2016
To use the blocks in Waterbear, there is a special function where you can put blocks within blocks themselves. This is a way
to add extra functionality to certain blocks. For example, to create a circle shape in Waterbear, there is already a block
created for the user to create a circle. However, to output the circle, there is another block labeled, 'draw the shape.'
That block takes a shape block, like our circle shape, and **then** draws the circle afterwards. This is but one of many ways to
draw out the circles, but that isn't the point here. 

The point is, is whenever the circle block is chosen, a variable block is already combined with the circle, causing problems
and confusion for users. The following is an excerpt from Waterbear's code and screenshot of the example:



[![Waterbear 1](https://github.com/huynhk3/waterbear/blob/master/example1.png)](#features)
======
[![Waterbear 2](https://github.com/huynhk3/waterbear/blob/master/example2.png)](#features)
======
[![Waterbear 3](https://github.com/huynhk3/waterbear/blob/master/example3.png)](#features)


                // Create variable block to wrap the expression.
                addBlockEvent = {
                    type: 'add-block',
                    addedBlock: null,
                    addedTo: dropTarget,
                    nextBlock: null,
                    originalParent: originalParent,
                    originalNextEl: nextElem
                };
                if (dragStart === 'script') {
                    addBlockEvent.type = 'add-var-block';
                    addBlockEvent.insideBlock = dragTarget;
                }
                addToContains(createVariableBlock(dragTarget), evt, addBlockEvent);


At the bottom, we can see that a variable block is added to certain blocks by default. I am proposing to not get rid of the 
variable block altogether, but to add functionality to distinguish on which parts of blocks can be added together to others.

		glowy {
			background-color: #ccc;
			border: 1px solid transparent;    
			-webkit-transition: border 0.1s linear, box-shadow 0.1s linear;
				-moz-transition: border 0.1s linear, box-shadow 0.1s linear;
					transition: border 0.1s linear, box-shadow 0.1s linear;
		}

		glowy.active {
			border-color: blue;
			-webkit-box-shadow: 0 0 5px blue;
				-moz-box-shadow: 0 0 5px blue;
					box-shadow: 0 0 5px blue;
		}

		$(function() {  
			var glower = $('glowy');
			window.setInterval(function() {  
				glower.toggleClass('active');
			}, 1000);
		});

I am a bit new with JS, but I think adding this glowing effect while the user clicks on certain blocks to see which can be combined 
what would be helpful in my opinion. That way, people can immediately figure out that the blocks are broken down in components,
and can be put into other glowing sections with other specific blocks.


# March 15, 2016
When working with Waterbear, a simple way to know if the application is working is having a simple print statement that usually
prints out, "Hello World!" Setting this up in Waterbear can be a little bit vague, but once you understand the basic functionality
of the website, then it should be a simple task. However, there is a small bug where when outputting text with the 'fill text'
block, which prints out text to the output window, where you cannot use the formatting parameters and blocks. Below is an issue
(https://github.com/waterbearlang/waterbear/issues/1324) I've posted to Waterbear's github:


[![Waterbear 1](https://github.com/huynhk3/waterbear/blob/master/example4.png)](#features)


In this picture, the bottom block is the one which outputs text, and the top block is the one which modifies the text. When
running the program with different values for the modifying block gives no results. This could be a bug with the blocks themselves
or perhaps the function to run the program, I suspect it to be the blocks though.

Looking closer at the code with debug in chrome, I noticed this anomaly:

[![Waterbear 1](https://github.com/huynhk3/waterbear/blob/master/example5.png)](#features)
[![Waterbear 1](https://github.com/huynhk3/waterbear/blob/master/example6.png)](#features)

When changing the value in the block, the value does change in the code, but does not change the px size at all. Perhaps this
is what is causing the problem? I suspect something is causing a problem with that specific class.
