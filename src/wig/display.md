The Sensor Watch Display
========================

Before we talk about the Sensor Watch display, let's go through some key terminology to clarify our discussion: 

* Segment - A single addressable element on the liquid crystal display
* Indicator - A segment like "PM", "24H" or the bell icon that indicates status
* Digit - A grouping of segments that can display a number, character or glyph
* Position - The placement of a digit on the display; for example, the first digit at the left of the top row is Position 0

We also tend to label the segments of each digit clockwise from the top segment: the top segment is segment A, top right is B, bottom right is C, all the way to the center digit which is segment G. 

![TODO: A diagram of a single digit with its segments labeled](https://via.placeholder.com/320x160?text=TODO)

The Sensor Watch has five indicators, ten digits, and one segment dedicated to the colon in the time display. We choose to number the digits as follows: 

* Positions 0-1 - The digits in the top middle, usually used to display the current mode or the weekday. We can call these the “Weekday” digits.
* Positions 2-3 - The digits at the top right, usually used to display the day of the month. The “Day” digits.
* Positions 4-9 - The digits on the bottom row, usually used to display the time; the “Clock” digits.
    * Positions 4-5 are normally the hours display. The digit in position 4 is slightly narrower than the others.
    * Positions 6-7 are normally the minutes display.
    * Positions 8-9 are normally the seconds display, and are slightly smaller than the other digits on the bottom row.

![TODO: A diagram of the F-91W LCD with positions grouped and labeled](https://via.placeholder.com/320x160?text=TODO)

As alluded to in the "Big Picture" section, this document is not going to be prescriptive about how you use the digits in these positions; there is no "must" about how you display information on your watch face. Still, there are some broad guidelines on where these digits can be most useful:

* The "Weekday" digits are particularly useful for displaying alphanumeric information.
* The "Day" digits are best for displaying a single number from 0-39, such as a day, an index or a countdown.
* The "Clock" digits are well suited for the main informational display of your watch face.

You are going to need flexibility to adapt the information you want to display to the Sensor Watch LCD. This section is merely going to walk through some useful patterns, some limitations, and some best practices. 

### The Weekday Digits

The digits in these first two positions, positions 0 and 1, have some extra segments that make them useful for displaying letters. The main watch face, like the stock F-91W, uses these positions to display the day of the week (SU, MO, TU, etc). If you have some alphanumeric information to relay on your watch face, it would make sense to look to these first; the tide prediction concept in the previous section, for example, imagined labeling the displayed prediction with "HT" for high tide and "LT" for low tide.

If you have no data to put in these segments, they can also serve as a useful spot to title your watch face, so that the wearer is clear what information they are looking at. The "Temperature" watch face, for example, uses these digits to display “TE”. This distinguishes it from the “Temperature Log” watch face, which titles itself “TL”.

Note that you are not limited to keeping the same characters in this position the whole time your watch face is on screen! The "Temperature Log" watch face displays "TL" most of the time, but when the wearer enters timestamp mode, it displays the word “At” in these positions, signaling that the data point was logged "at" the displayed time and date. 

![Rendering: a temperature logging app, showing the logged temperature of 68.7 degrees Fahrenheit, and a 0 at the top right. A second screen to the right displays "At 12:00" with a 25 at the top right](images/temperature-log-app-timestamp.png)

Consider: when the wearer presses the "Mode" button and sees the watch face for the first time, “TL” tells them which watch face they are viewing. Once they have that information, they know they will remain in this watch face until they press "Mode" again, so you can feel free to change it after a short delay or in response to a button press. It's done its job, and given the wearer the context they need to use the watch in the current mode.

Of course, you could use these segments in a completely different way. The LIS2DH accelerometer test face (which counts three minutes' worth of accelerometer interrupts on the Clock line) uses these two positions to indicate the presence of an interrupt on the X or Y axes, lighting up "Y" and/or "X" when an interrupt is asserted, and remaining blank otherwise.

![TODO: Two watch images: the accelerometer watch face displaying a Y interrupt, and an X and Y interrupt](https://via.placeholder.com/320x160?text=TODO)

#### Limitations of the Weekday Digits

On a stock Casio F-91W, the digits in these two positions normally display one of just nine values: abbreviations for the seven days of the week, the text "AL" for alarm mode, or the text "ST" for stopwatch mode. If you break this down, position 0 will only ever display one of the characters A, F, M, S, T or W, and position 1 will only display the letters A, E, H, L, O, R, T, or U. The Sensor Watch aims to display many more characters in these positions, and in the case of position 0, we can do it! With the exception of an uppercase R, the digit in position 0 can display any character in the Sensor Watch character set.

![TODO: A diagram of the F-91W's Weekday Digits with position's 1 shared segments highlighted in red.](https://via.placeholder.com/320x160?text=TODO)

Position 1 is a bit more trouble. Looking closely at the position 1 letters above, you'll notice that segments B/C and E/F never have to operate independently (as they would to, say, display the letter "S" or the number 2). Thus, to save pins on the LCD, the designers of the F-91W tied these two segments together. This means you can only display a limited set of characters in position 1: the letters A, B, C, D, E, F, H, I, J, L, N, O, R, T, U and X, and the numbers 0, 1, 3, 7 and 8. The fact is, the Sensor Watch repurposes a display from a stock F-91W wristwatch, which wasn't designed for our use case. We can get away with quite a lot, but there are a few things we can't work around.

This means that you may need to think about terminology that makes sense for your watch face, and tweak it to fit the constraints. For example, the "Settings" watch face requires changing a setting related to Movement's low power mode, but the P in "LP" cannot be displayed in position 1. To address this limitation, the setting is instead called "Low Energy" mode, which abbreviates to "LE".

The theme of limitations will come up in each of these groups.

### The Day Digits

On a stock Casio F-91W, these two digits normally display the day of the month. This makes this position very useful for displaying values from 0-39:

* The Clock and World Clock face use this area to display the day of the month.
* The TOTP watch face uses this area for a 30-second countdown, indicating the validity window for the displayed code
* The Temperature Log uses this area to display the index of the logged measurement, from 0 to 35

![TODO: Three watch faces showing these uses.](https://via.placeholder.com/320x160?text=TODO)

This section is short because the fact is, there's not a lot to do in these segments. If you have a date or an index from 0 to 39, you can dis

#### Limitations of the Day digits

While the digit at position 3 is a full-featured 7-segment display that can display any number and just about any letter, the digit in position 2 is the most limited segment on the watch: it can only display the numbers 1, 2 and 3. This constraint related to the fact that it is missing one segment (segment F), and that sefments A, D and G are all tied together.

There's not much to say about these digits because they are pretty limited: if you have a single letter or a number from 0-39, you can display it here. If not, you can leave these digits blank.

### The Clock Digits

TODO