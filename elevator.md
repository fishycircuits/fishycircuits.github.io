This is a working 5-story elevator. It is 3 feet tall. We put a lot of work into this.

Let's cut to the chase ... here's how it works!

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/hPx-92t-4RI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Quick links:
<ul>
 	<li><a href="https://drive.google.com/file/d/0Bxsjrwz9nUp_N3VNSkoyTUpMbTQ/view?usp=sharing">Code</a></li>
 	<li>Wiring diagram (coming soon)</li>
</ul>
<h2>Inspiration</h2>
We've been playing with Arduino and embedded processing/IoT for a couple of years now, but most projects we have done (and most we have seen) are pretty simple. We've been looking for something "real" to do for a long time.

This summer, I went to an awesome summer camp, <a href="http://projectember.org">Project Ember</a>. It is in the San Francisco Bay Area and it is awesome! Kids design and build large wood structures with power tools. Once I knew I could do that, I wanted to combine the physical building with Arduino and this is the outcome!
<h2>Approach</h2>
The hardest part of figuring this out was the motor and floor detection technique. A real elevator probably uses a huge A/C motor with sensors at each floor location. We certainly could use this approach with a smaller-scale but putting sensors at each floor is a lot of wiring, and we would have concerns about sensitivity and alignment, etc. On the other hand, a stepper motor can be positioned precisely ... but we would have to know exactly where we are and how far we have to go to do that.

Fortunately, we have done something similar, in our earlier "<a href="https://fishycircuits.wordpress.com/2017/06/17/calendar/">fancy calendar</a>" project. There, we had figured out how to use stepper motors and more interestingly, to save their positions in non-volatile memory (EEPROM on the Arduino). So we'll use the same approach here. This way we don't need any position sensors at all, we'll just count on our ability to count the number of steps that we move our stepper motor.

The other design concern was with the elevator call buttons. They need to be lit momentary contact switches, but the lights need to be controllable independently from the button. We found some suitable ones <a href="http://www.ebay.com/itm/20Pack-Momentary-1NO-1NC-AC-3A-250V-Push-Button-Square-Switch-w-LED-Light/292094184237?ssPageName=STRK%3AMEBIDX%3AIT&amp;_trksid=p2057872.m2749.l2649">on eBay</a>.
<h2>Materials</h2>
<ul>
 	<li>An Arduino Mega2560 - we chose this because it had more GPIO pins for all the bells and whistles in the project. <a href="https://store.arduino.cc/usa/arduino-mega-2560-rev3" target="_blank" rel="noopener">Buy Official</a> - you may be able to get an imitation/compatible cheaper.</li>
 	<li>An 8x8 LED matrix to show arrows <a href="https://www.amazon.com/dp/B00TNNDH0A/ref=asc_df_B00TNNDH0A5073783/?tag=hyprod-20&amp;creative=395033&amp;creativeASIN=B00TNNDH0A&amp;linkCode=df0&amp;hvadid=194017009123&amp;hvpos=1o2&amp;hvnetw=g&amp;hvrand=10320582608361537086&amp;hvpone=&amp;hvptwo=&amp;hvqmt=&amp;hvdev=c&amp;hvdvcmdl=&amp;hvlocint=&amp;hvlocphy=9031913&amp;hvtargid=pla-309635910376">Buy (Amazon)</a></li>
 	<li>A seven-segment display to show the floor numbers <a href="https://www.sparkfun.com/products/8546">Buy (SparkFun)</a></li>
 	<li>A stepper motor and driver board to move the car <a href="https://www.elegoo.com/product/elegoo-5-sets-28byj-48-5v-stepper-motor-uln2003-motor-driver-board-for-arduino/">Buy 5-pack (Elegoo)</a> Note: you only use one, but you may need more. And you can reuse the box they come in. :-)</li>
 	<li>A Mega2560 protoboard, to connect our wires <a href="https://www.banggood.com/Mega2560-1280-Proto-Shield-V3-Proto-Expansion-Board-With-Breadboard-p-916227.html">Buy (BangGood)</a> We desoldered the header on top, you don't have to.</li>
 	<li>Buttons with separate lights (We bought from eBay, they should look like:[gallery ids="162,161,160" type="circle" orderby="rand"]</li>
 	<li>Screw terminals (10x2) <a href="http://www.frys.com/product/1899018">Buy (frys.com)</a> <strong>You will need 4</strong></li>
 	<li>Thread spool</li>
</ul>
<span style="text-decoration: underline;">You can find all of the materials below at your local Home Depot or other home improvement store:</span>
<ul>
 	<li>Fiberboard and 3/4 sq in moulding for the elevator and car.</li>
 	<li>Aluminum angle bracket to hold the motor</li>
 	<li>Assorted screws</li>
 	<li>Hose to act as bushing inside spool</li>
 	<li>String (we used heavy-duty nylon kite string)</li>
</ul>
<h2>Build</h2>
We made the shaft and car out of fiberboard and moulding to reinforce the corners.

We started with the elevator shaft. We cut 3 pieces of fiberboard to 36"x8" for the sides and rear (the front is open). Then using 4 pieces of 3/4" square moulding, 36" long, we screwed the fiberboard together to make a vertical shaft. Square pieces of fiberboard on the top and bottom holds everything square.

The elevator car is next. It uses the same sort of construction, with fiberboard walls, ceiling, and floors, and pine moulding supports. It is almost the full width of the shaft, but rides between the pine front and back (so it's wider than it is deep). We attached an eye hook to the top of the car, so that it hangs from a string.

<img class="alignnone size-medium wp-image-168" src="https://fishycircuits.files.wordpress.com/2017/06/img_2193.jpg?w=225" alt="" width="225" height="300" />

Make sure not to put a bottom on your shaft too early, because you need to be able to get the car in and out! Once testing is complete, you can add the bottom.

The motor sits on top of the elevator. We attached a regular wood spool (from sewing thread) to the shaft on the motor. This is a bit tricky. The motor shaft has a flat edge but of course the hole in the spool is round. So we drilled and tapped out a hole in the spool, and put a screw though to hold against the flat edge of the motor shaft. Also, the hole in the spool is larger than the motor shaft. To act as a bushing to take up the space, we used a very short piece of appropriately sized rubber hose.

<img class="alignnone size-medium wp-image-173" src="https://fishycircuits.files.wordpress.com/2017/06/img_2188.jpg?w=300" alt="" width="300" height="225" /> <img class="alignnone size-medium wp-image-174" src="https://fishycircuits.files.wordpress.com/2017/06/img_2187.jpg?w=300" alt="" width="300" height="225" />

Then we mounted the motor to a piece of angle aluminum and screwed that to the top of the shaft. To support the other side of the spool, we put a screw through a second piece of angle aluminum. This makes it so that the weight of the elevator won't pull the spool off of the motor shaft, it will stay level.

We used more fiberboard to make the button panels. On the left, we used a board the height of the shaft for the call buttons. We used alternating red and green buttons. Red for down, green for up. The top floor has only a red and the bottom has only a green. Our ''in elevator'' panel is on the right. We cut holes for the LED matrix and seven-segment display in addition to the 5 holes for the buttons.

<img class="alignnone size-medium wp-image-168" src="https://fishycircuits.files.wordpress.com/2017/06/img_2193.jpg?w=225" alt="" width="225" height="300" /> <img class="alignnone size-medium wp-image-169" src="https://fishycircuits.files.wordpress.com/2017/06/img_2192.jpg?w=225" alt="" width="225" height="300" />

We mounted 4 screwboxes. Two on the call panel, and two on the side next to the "inside-"elevator panel.
<h2>Wiring</h2>
&nbsp;

The wiring is tricky because there is a lot of it! We chose to use an Arduino Mega prototyping shield, partly because we already had one :-). But the real motivation was that with so many wires, we were concerned that something would inevitably become disconnected if we just used the standard Arduino pin connections. With the prototyping shield, we could solder wires directly and avoid that risk. In addition, it gave us a convenient place to put things like resistors, which are necessary for our 7-segment display.

<img class="alignnone size-medium wp-image-175" src="https://fishycircuits.files.wordpress.com/2017/06/img_2186.jpg?w=300" alt="" width="300" height="225" />

That said, we didn't want all of these different panels hardwired together, because if we made a mistake, it would be very hard to fix. So every wire has some sort of removable end on it. We used screw blocks between the switch panels and the Arduino, and for the 7-segment and LED matrix, one end of the wire are still quick-disconnect pins.

<img class="alignnone size-medium wp-image-171" src="https://fishycircuits.files.wordpress.com/2017/06/img_2190.jpg?w=225" alt="" width="225" height="300" />

For the button panels, we made our own wiring harnesses, using crimp-on female spade connectors which fit perfectly onto the button terminals. Because each button needed two grounds (one for the button and a separate one for the light), there would have been a LOT of ground wires if we ran them all to the Arduino. So instead we daisy-chained them all together with a nice custom wiring harness. The signal pins (one for the switch and one for the light on each button) are all separate, running to the screw blocks.

<img class="alignnone size-medium wp-image-172" src="https://fishycircuits.files.wordpress.com/2017/06/img_2189.jpg?w=225" alt="" width="225" height="300" /> <img class="alignnone size-medium wp-image-170" src="https://fishycircuits.files.wordpress.com/2017/06/img_2191.jpg?w=225" alt="" width="225" height="300" />

Finally, the screw blocks gave us another advantage -- we used solid-core wire to solder to the prototyping shield, but we used stranded wire for the crimp-on connectors to the backs of the buttons. The screw blocks gave us a place to switch from one to the other without soldering.
<h2>Programming</h2>
We had many revisions of code, but here is the current version. The most complicated part of the software is the logic to figure out where the elevator car should go. If it's on floor 2, someone inside wants to go to 3, someone wants to go down from 4 and up from 1 ... where do you go first?

The other complicated part is that the way that the stepper motor library normally works is that during the time that the motor is moving, nothing is calling the Arduino "loop()" function. Yet, it should work for someone to press a button while the elevator is in transit. So you can't go all the way to the destination in a single step -- you need to move a bit at a time, checking for button presses (and possibly changes in destination) along the way.

You can download our Arduino sketch <a href="https://drive.google.com/file/d/0Bxsjrwz9nUp_N3VNSkoyTUpMbTQ/view?usp=sharing">here.</a>

To upload the code:
<ol>
 	<li>Download the Arduino IDE. <a href="https://www.arduino.cc/en/Main/Software" target="_blank" rel="noopener">arduino.cc</a></li>
 	<li>Open the code.</li>
 	<li>You will need to download these libraries:
<ol>
 	<li><a href="https://github.com/shaai/Arduino_LED_matrix_sketch">LEDControlMS</a></li>
 	<li><a href="https://github.com/sigvaldm/SevenSeg">SevenSeg</a></li>
</ol>
</li>
 	<li>To install libraries, see <a href="https://www.arduino.cc/en/Guide/Libraries#toc4" target="_blank" rel="noopener">this tutorial</a>.</li>
 	<li>Upload the code:
<ol>
 	<li>Choose the right board: <a href="https://fishycircuits.files.wordpress.com/2017/07/screen-shot-2017-07-13-at-12-34-17-pm.png">See this image</a></li>
 	<li>Choose the port: Similar, but you go to "Port". On MacOS, it will be something like /dev/cu.usbmodem1411, while on Windows, it will be something like COM2.</li>
 	<li>Upload your code. <img class="alignnone size-full wp-image-154" src="https://fishycircuits.files.wordpress.com/2017/06/uploadicon.png" alt="uploadicon" width="306" height="52" /></li>
</ol>
</li>
 	<li>The elevator should go through its self-test. All the call buttons should light in sequence, then the five in-elevator buttons, then the seven segment display should cycle, then the matrix should show up and down arrows. Once complete, the 7-segment display will show the last known floor number of the elevator car.</li>
 	<li>If it did, congratulations! Move on to testing. If it didn't, go back to step 5. If that didn't work again, double-check your wiring. If <em>that</em> didn't work, contact us using the link at the top.</li>
</ol>
<h2>Testing/Calibrating</h2>
Because the stepper motor needs to know exactly where to stop for each floor, you need to manually tell it - once. It will remember this in non-volatile memory (meaning that it will save it even when power is disconnected).

To calibrate:
<ol>
 	<li>Press and hold the top and bottom buttons on the right panel. The matrix should show a C (for calibrate).</li>
 	<li>Use those top and bottom buttons to manually move the car to the floor shown on the seven segment. When it is in the right place, press the middle button.</li>
 	<li>Repeat step 2 for all five floors. When you are done, the matrix should turn off.</li>
</ol>
<h2>Next Steps</h2>
Projects like this are never truly done! We would like to rebuild the structure of the elevator and shaft with laser-cut parts. We used a handheld jigsaw to do this and so our cuts are not really all that straight ... that is partially what is causing our "friction problem". At the same time, we would design a better motor mount and get a better, faster motor.

Electronically, we have had a request to add a bell or chime for each time the elevator door is opening, as many real elevators do. We'll do that too.

Any thoughts or suggestions on this project, please let us know!
<h2>Version History</h2>
Note: The Google Drive link will automatically update with each version.

Version 2: We fixed the bug where calling the elevator from outside on the current floor may cause the software to hang, requiring you to push the reset button.
