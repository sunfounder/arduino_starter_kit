11. Conditional LED Control
==================================

Welcome to our interactive tutorial on mastering conditional statements for controlling LEDs! This course is designed to take you from basic to advanced techniques, helping you understand how to make LEDs respond dynamically to the input from a potentiometer. Whether you're a beginner looking to learn about if statements or an experienced coder ready to tackle if-else if-else structures, this course offers step-by-step guidance on creating engaging and visually informative setups. By the end of this course, you'll be able to program LEDs to indicate different levels of input, making them not just light up, but tell a story.


``if`` Statements
-----------------------

1. Open the sketch you saved earlier, ``Lesson5_Serial``. Hit "Save As..." from the "File" menu, and rename it to ``Lesson5_if``. Click "Save".

2. From Lesson 4, you learned about conditional statements, sometimes referred to as if statements. These statements execute certain lines of code when a condition is true. The basic form of a conditional statement is:

.. code-block:: Arduino

    if (condition) {
        Commands to execute when condition is true  
    }

The ``readValue`` variable is an analog value determined by the potentiometer ranging from 0 to 1,023. At the higher end of this range, the LED light is brightest. Create a condition for the LED when the ``readValue`` variable is greater than or equal to 1,000. Type the following ``if`` statement in your ``void loop()`` function:

.. code-block:: Arduino
    :emphasize-lines: 8-10   

    void loop() {
        readValue = analogRead(A0);    // Read value from potentiometer
        writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
        analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
        analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
        analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
        
        if (readValue > 1000) {
            
        }
        
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }
.. note::

    You may wonder why we set the flashing threshold at 1,000 instead of the maximum 1,023. This is because potentiometers can vary slightly due to manufacturing tolerances—even though they're rated from 0 to 10,000 ohms, the actual range might be slightly off, such as 10 to 9,600 ohms. Setting the threshold at 1,000 ensures there's a consistent range for the flashing behavior. 
    
    If the LEDs still don't flash, try adjusting the threshold down, perhaps to 900, after checking the maximum value by rotating the potentiometer.

3. Within the ``if`` statement's curly braces, you can add commands to execute when the condition is met. For example, to make the LEDs flash when the potentiometer's value exceeds 1,000, you can use the ``digitalWrite()`` command, which you learned in Lesson 4. This command turns LEDs on or off by setting the designated pins—9, 10, and 11—to ``LOW`` or ``HIGH``.

.. code-block:: Arduino
    :emphasize-lines: 8-10   

    void loop() {
        readValue = analogRead(A0);    // Read value from potentiometer
        writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
        analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
        analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
        analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
        if (readValue > 1000) {
            digitalWrite(9,LOW);          // Switch off the LED on pin 9
            digitalWrite(10,LOW);         // Switch off the LED on pin 10
            digitalWrite(11,LOW);         // Switch off the LED on pin 11 
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }

.. note::

    * Notice how commands inside the curly braces of the ``if`` statement are indented. Indentation helps you easily identify the commands that are executed when the condition is true.
    * Besides using ``digitalWrite(pin, LOW)`` to turn off the LEDs, you can also use ``analogWrite(pin, 0)``. Both commands have the same effect on the LEDs.

4. To make the LEDs flash, they must be turned off for a short period before lighting up again. You can use the ``delay()`` function to pause the code for 250 milliseconds (a quarter of a second).

.. code-block:: Arduino
    :emphasize-lines: 11 

    void loop() {
        readValue = analogRead(A0);    // Read value from potentiometer
        writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
        analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
        analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
        analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
        if (readValue > 1000) {
            digitalWrite(9,LOW);          // Switch off the LED on pin 9
            digitalWrite(10,LOW);         // Switch off the LED on pin 10
            digitalWrite(11,LOW);         // Switch off the LED on pin 11
            delay(250);                    // Wait for 0.25 seconds 
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }


5. Now that the LEDs are off, use three ``digitalWrite()`` commands to light them up again. You can copy the commands that turn off the 3 LEDs and change ``LOW`` to ``HIGH`` to achieve this.

.. code-block:: Arduino
    :emphasize-lines: 22-25 

    int readValue = 0;
    int writeValue = 0;

    void setup() {
        pinMode(9, OUTPUT);   // Set pin 9 as output
        pinMode(10, OUTPUT);  // Set pin 10 as output
        pinMode(11, OUTPUT);  // Set pin 11 as output
        Serial.begin(9600);   // Initialize serial communication at 9600 baud
    }
    
    void loop() {
        readValue = analogRead(A0);    // Read value from potentiometer
        writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
        analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
        analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
        analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
        if (readValue > 1000) {
            digitalWrite(9,LOW);          // Switch off the LED on pin 9
            digitalWrite(10,LOW);         // Switch off the LED on pin 10
            digitalWrite(11,LOW);         // Switch off the LED on pin 11
            delay(250);                    // Wait for 0.25 seconds 
            digitalWrite(9,HIGH);          // Light up the LED on pin 9
            digitalWrite(10,HIGH);         // Light up the LED on pin 10
            digitalWrite(11,HIGH);         // Light up the LED on pin 11
            delay(250);                    // Wait for 0.25 seconds 
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }

6. Your code is now basically finished. You can click Upload to upload the code to the R3 board.

7. Now, turn the potentiometer while opening the serial monitor to see the current analog value. You will notice that when the analog value exceeds 1000, the LEDs start to flash.

``if-else`` Statements
--------------------------

In addition to basic conditional statements, there are more complex conditions that let you evaluate multiple conditions. An ``if-else`` statement will run one set of commands if the condition is true, and another set of commands under the ``else`` clause if the condition is false. The structure of an ``if-else`` statement is:

.. code-block:: Arduino

    if (condition) {
        Commands to execute when condition is true
    } else {
        Commands to execute when condition is false
    } 
  
We can rewrite the previous code using ``if-else`` to achieve the same effect.

* Make the LEDs flash when the variable ``readValue`` is greater than 1000.
* Otherwise, adjust the LEDs' brightness based on ``readValue / 4``.

1. Open the sketch you saved earlier, ``Lesson5_if``. Hit "Save As..." from the "File" menu, and rename it to ``Lesson5_if_else``. Click "Save".

2. Add an ``else`` clause after the ``if`` statement. Ensure you include both left and right braces.


.. code-block:: Arduino
    :emphasize-lines: 11,12

    ...
    if (readValue > 1000) {
        digitalWrite(9, LOW);    // Switch off the LED on pin 9
        digitalWrite(10, LOW);   // Switch off the LED on pin 10
        digitalWrite(11, LOW);   // Switch off the LED on pin 11
        delay(250);              // Wait for 0.25 seconds
        digitalWrite(9, HIGH);   // Light up the LED on pin 9
        digitalWrite(10, HIGH);  // Light up the LED on pin 10
        digitalWrite(11, HIGH);  // Light up the LED on pin 11
        delay(250);              // Wait for 0.25 seconds
    } else {
    }
    Serial.print("Read Value: ");  // Prompt for the read value
    Serial.println(readValue);     // Print the potentiometer value
    delay(100);                    // Wait for 0.1 seconds
    }

2. Cut the three ``analogWrite()`` statements near the top of your ``void loop()`` function and paste them inside the braces of the ``else {}`` part of your ``if-else`` statement as shown below.

.. code-block:: Arduino
    :emphasize-lines: 24,25,26

    int readValue = 0;
    int writeValue = 0;

    void setup() {
        pinMode(9, OUTPUT);   // Set pin 9 as output
        pinMode(10, OUTPUT);  // Set pin 10 as output
        pinMode(11, OUTPUT);  // Set pin 11 as output
        Serial.begin(9600);   // Initialize serial communication at 9600 baud
    }

    void loop() {
        readValue = analogRead(A0);  // Read value from potentiometer
        writeValue = readValue / 4;  // Scale readValue to fit LED brightness range
        if (readValue > 1000) {
            digitalWrite(9, LOW);    // Switch off the LED on pin 9
            digitalWrite(10, LOW);   // Switch off the LED on pin 10
            digitalWrite(11, LOW);   // Switch off the LED on pin 11
            delay(250);              // Wait for 0.25 seconds
            digitalWrite(9, HIGH);   // Light up the LED on pin 9
            digitalWrite(10, HIGH);  // Light up the LED on pin 10
            digitalWrite(11, HIGH);  // Light up the LED on pin 11
            delay(250);              // Wait for 0.25 seconds
        } else {
            analogWrite(9, writeValue);   // Apply brightness to LED on pin 9
            analogWrite(10, writeValue);  // Apply brightness to LED on pin 10
            analogWrite(11, writeValue);  // Apply brightness to LED on pin 11
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }

3. Click the “Upload” button to upload your sketch to the R3 board.

4. Rotate the potentiometer and simultaneously observe the analog value in the serial monitor. You will also find that when the analog value exceeds 1000, the LEDs start flashing; otherwise, the LEDs’ brightness will change as the potentiometer is rotated.

``if-else if-else`` Statement
------------------------------

Complex conditions in programming allow you to make decisions based on multiple scenarios using ``if-else if-else`` structures.

Take LED arrays as an example. These are often used in audio mixers as VU meters to show volume levels, lighting up more LEDs as the volume increases. In this lesson, you will program LEDs to respond to a potentiometer's value, lighting up sequentially as it's turned up.


1. Remember from Lesson 4 how you wrote pseudocode. Pseudocode is like an outline for a program or sketch, written in everyday language that is easy to understand. Soon, you'll write pseudocode to create an LED array that displays the value of the potentiometer. As the potentiometer is turned up, the LEDs light up sequentially. But before you write pseudocode, consider these questions:

.. code-block::

    - How does the Arduino know the value from the potentiometer?
    - How do you control the brightness of each LED?
    - How can you turn off all LEDs if the potentiometer is dialed down completely?
    - What commands light up the LEDs based on the potentiometer's value?

2. Please write your pseudocode for the LED indicator array on the blank space provided in Lesson 5.4 of your handbook.

3. To convert your pseudocode into a sketch, start by revising your last sketch, open the previously saved sketch ``Lesson5_if_else``.
4. Use the "Save As..." option in the "File" menu to rename it to ``Lesson5_if_else_if`` and save.

5. To sequentially light up each LED based on the value of the potentiometer, you will need multiple conditions. You can use ``if`` to specify actions for different ranges of potentiometer values:
  
  - Below 200: Turn off all LEDs.
  - Between 200 and 600: Light up the first LED.
  - Between 600 and 1000: Light up two LEDs.
  - Above 1000: Light up all LEDs.

However, managing these conditions separately can be inefficient, as Arduino needs to check each one in every loop cycle. 

To streamline this, utilize the ``if-else if`` structure:

.. code-block:: Arduino

    if (condition 1) {
        // Execute if condition 1 is true
    }
    else if (condition 2) {
        // Execute if condition 2 is true
    }
    else if (condition 3) {
        // Execute if condition 3 is true
    }
    else {
        // Execute if none of the conditions are true
    }

In an ``if-else if`` structure, the first condition is tested. If it's true, the associated commands are executed, and all other conditions are skipped (even if some of them are true). If the first condition is false, it tests the second condition in the structure. If the second condition is true, it executes the commands associated with this condition and then skips the others. If it is false, it tests the third condition, and so on. In some scenarios, there can be multiple true conditions. Therefore, the order of conditions is important. Only the first true condition will have its associated commands run.

6.  Now modify the ``if`` statement in your ``void loop()`` to the following. Turn off all three LEDs if the value of the potentiometer is less than 200.

.. code-block:: Arduino
    :emphasize-lines: 4-7 
    
    void loop() {
        readValue = analogRead(A0);  // Read value from potentiometer
        writeValue = readValue / 4;  // Scale readValue to fit LED brightness range
        if (readValue < 200) {       // If readValue less than 200
            digitalWrite(9, LOW);      // Switch off the LED on pin 9
            digitalWrite(10, LOW);     // Switch off the LED on pin 10
            digitalWrite(11, LOW);     // Switch off the LED on pin 11
        } else {
            analogWrite(9, writeValue);   // Apply brightness to LED on pin 9
            analogWrite(10, writeValue);  // Apply brightness to LED on pin 10
            analogWrite(11, writeValue);  // Apply brightness to LED on pin 11
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }

7.  Add an ``else if`` statement to light up the first LED when the potentiometer's analog value is below 600:


.. code-block:: Arduino
    :emphasize-lines: 8-11 
    
    void loop() {
        readValue = analogRead(A0);  // Read value from potentiometer
        writeValue = readValue / 4;  // Scale readValue to fit LED brightness range
        if (readValue < 200) {       // If readValue less than 200
            digitalWrite(9, LOW);      // Switch off the LED on pin 9
            digitalWrite(10, LOW);     // Switch off the LED on pin 10
            digitalWrite(11, LOW);     // Switch off the LED on pin 11
        } else if (readValue < 600) {       // If readValue less than 600
            digitalWrite(9, HIGH);      // Light up the LED on pin 9
            digitalWrite(10, LOW);     // Switch off the LED on pin 10
            digitalWrite(11, LOW);     // Switch off the LED on pin 11
        } else {
            analogWrite(9, writeValue);   // Apply brightness to LED on pin 9
            analogWrite(10, writeValue);  // Apply brightness to LED on pin 10
            analogWrite(11, writeValue);  // Apply brightness to LED on pin 11
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }


8. To light up two LEDs when the value is below 1000, insert another ``else if`` condition like this:

.. code-block:: Arduino
    :emphasize-lines: 7-10 
    
    ...
        } else if (readValue < 600) {       // If readValue less than 600
            digitalWrite(9, HIGH);      // Light up the LED on pin 9
            digitalWrite(10, LOW);     // Switch off the LED on pin 10
            digitalWrite(11, LOW);     // Switch off the LED on pin 11
        } else if (readValue < 1000) {       // If readValue less than 1000
            digitalWrite(9, HIGH);      // Light up the LED on pin 9
            digitalWrite(10, HIGH);     // Light up the LED on pin 10
            digitalWrite(11, LOW);     // Switch off the LED on pin 11
    ...


9. Finally, modify the commands inside the ``else`` block to light up all three LEDs using ``digitalWrite()``. This block contains commands that run when none of the other conditions are true. In other words, if the ``readValue`` from the potentiometer is greater than or equal to 1000, the commands within ``else {}`` will execute. Your ``else`` block should look like this:

.. code-block:: Arduino
    :emphasize-lines: 27-29 

    int readValue = 0;
    int writeValue = 0;

    void setup() {
        pinMode(9, OUTPUT);   // Set pin 9 as output
        pinMode(10, OUTPUT);  // Set pin 10 as output
        pinMode(11, OUTPUT);  // Set pin 11 as output
        Serial.begin(9600);   // Initialize serial communication at 9600 baud
    }

    void loop() {
        readValue = analogRead(A0);     // Read value from potentiometer
        writeValue = readValue / 4;     // Scale readValue to fit LED brightness range
        if (readValue < 200) {          // If readValue less than 400
            digitalWrite(9, LOW);         // Switch off the LED on pin 9
            digitalWrite(10, LOW);        // Switch off the LED on pin 10
            digitalWrite(11, LOW);        // Switch off the LED on pin 11
        } else if (readValue < 600) {   // If readValue less than 600
            digitalWrite(9, HIGH);        // Light up the LED on pin 9
            digitalWrite(10, LOW);        // Switch off the LED on pin 10
            digitalWrite(11, LOW);        // Switch off the LED on pin 11
        } else if (readValue < 1000) {  // If readValue less than 1000
            digitalWrite(9, HIGH);        // Light up the LED on pin 9
            digitalWrite(10, HIGH);       // Light up the LED on pin 10
            digitalWrite(11, LOW);        // Switch off the LED on pin 11
        } else {
            digitalWrite(9, HIGH);   // Light up the LED on pin 9
            digitalWrite(10, HIGH);  // Light up the LED on pin 10
            digitalWrite(11, HIGH);  // Light up the LED on pin 11
        }
        Serial.print("Read Value: ");  // Prompt for the read value
        Serial.println(readValue);     // Print the potentiometer value
        delay(100);                    // Wait for 0.1 seconds
    }

10. Once your code looks like the structure above, click "Upload" to send the code to your R3 board.

11. Rotate the potentiometer to see if the LED array functions as expected:

   - If the potentiometer's value is below 200, all LEDs should be off.
   - If the value is between 200 and 600, the first LED should be on.
   - If the value is between 600 and 1000, the first two LEDs should be on.
   - If the value exceeds 1000, all LEDs should be on.

**Summary**

Throughout this course, we've explored various ways to use conditional statements to control LEDs, starting from simple ``if`` conditions to more complex ``if-else if-else`` configurations. Each lesson built upon the last, culminating in the ability to create a dynamic LED indicator system that reacts to the changes in potentiometer values. You've learned not only to program basic on/off states but also to implement scenarios where multiple LEDs can represent different thresholds of analog input values.

By mastering these conditional statements, you're now better equipped to handle a variety of programming challenges and ready to delve into more advanced projects that involve intricate logic and multiple outputs.

**Question:**

In the last code, we determine the number of LEDs to light up based on the value of the potentiometer. How can we modify the code so that, while lighting up the LEDs, their brightness changes in accordance with the potentiometer?