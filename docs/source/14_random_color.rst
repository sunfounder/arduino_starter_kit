14. Random Colors
======================

Sometimes, life needs a dash of surprise. When you're feeling indecisive, let randomness take the reins. This lesson will guide you on how to make an RGB LED light up in random colors, perfect for when you want to add an unpredictable sparkle to your projects.

Building the Circuit
-----------------------

**Components Needed**

.. list-table:: 
   :widths: 25 25 25 25
   :header-rows: 0

   * - 1 * R3 Board
     - 1 * RGB LED
     - 3 * 220Ω Resistor
     - Jumper Wires
   * - |compoents_uno_r3| 
     - |compoents_rgb_led| 
     - |compoents_220ohm| 
     - |compoents_wire| 
   * - 1 * USB Cable
     - 1 * Breadboard
     - 1 * Multimeter
     -
   * - |compoents_usb_cable| 
     - |compoents_breadboard| 
     - |compoents_meter|
     -
     
This lesson uses the same circuit as Lesson 12.

.. image:: img/6_mix_color_bb_4.png
    :width: 600
    :align: center

Code Creation
-------------------

In the previous lessons, you've controlled the RGB LED to display your desired colors. But sometimes, you may not need it to show a specific color; instead, you might want it to display a random color, much like stage lights. How can this be done?

**Know random() functions**

In the physical world, randomness abounds, but in programming, so-called "random" numbers are usually computed through a deterministic algorithm. This algorithm typically requires a starting point known as a "seed," making these numbers predictable and thus called "pseudo-random." The "pseudo" prefix indicates that these numbers seem random but are actually patterned.

Interestingly, on an R3 board, we can use physical measurements from the real world as seeds. During your measurements with a multimeter, you might notice minor fluctuations in the circuit's voltage and current values. These fluctuations can provide unpredictability to our random numbers.

Arduino's approach to randomness involves several functions:

* ``randomSeed();``: Initializing the random number generator's seed value. This function ensures that the starting point of the random number sequence varies with each program run, thus producing different sequences. 

    **Parameters**
        * ``seed``: A value used to initialize the random number generator. This unsigned long value sets the starting point of the random sequence.
    **Returns**
        None.

* ``long random(long max);``: Generating a random number within a specified range.

    **Parameters**
        ``max``: The upper limit of the random number (``max`` itself not included), meaning the random number will be between 0 (inclusive) and ``max-1`` (inclusive).
    
    **Returns**
        A long type number between 0 and max-1.

* ``long random(long min, long max);``: Generating a random number within a specified range.

    **Parameters**
        ``min``: The lower limit of the random number (inclusive).
        ``max``: The upper limit of the random number (``max`` itself not included), meaning the random number will be between min (inclusive) and max-1 (inclusive).
    
    **Returns**
        A long type number between min and max-1.

**Writing the Code**

1. If necessary, open your ``Lesson13_PWM_Color_Mixing`` sketch in the Arduino IDE.

2. Save the sketch under a new name. From the "File" menu, select "Save As...", and the sketch location should default to the Arduino Sketchbook. Name the file ``Lesson14_Random_Colors``. Click "Save".

3. Only call ``randomSeed()`` once in ``void setup()`` to initialize the seed. Avoid using a fixed seed value, as this would cause the same sequence of random numbers to be generated every time the program runs.

    We use ``analogRead(0)`` to read the value from an unconnected analog pin. As this pin is not connected, it picks up noise, which varies with each reading, providing a good seed for ``randomSeed()``.

.. code-block:: Arduino
    :emphasize-lines: 9

    void setup() {
        // Set up code to run once:
        pinMode(9, OUTPUT);   // Set Blue pin of RGB LED as output
        pinMode(10, OUTPUT);  // Set Green pin of RGB LED as output
        pinMode(11, OUTPUT);  // Set Red pin of RGB LED as output
            
        // Initialize random seed based on an unconnected analog pin
        // This ensures a different sequence of random numbers on each reset
        randomSeed(analogRead(0));
    }

4. Now in ``void loop()``, remove the original code. Use the ``random()`` function to generate random values stored in the variables ``redValue``, ``greenValue``, and ``blueValue``.

.. code-block:: Arduino
    :emphasize-lines: 3-5

    void loop(){
        // Generate random values for each color component
        int redValue = random(0, 256);   // Random value between 0 and 255
        int greenValue = random(0, 256); // Random value between 0 and 255
        int blueValue = random(0, 256);  // Random value between 0 and 255
    }

5. Input the generated RGB values into the ``setColor()`` function, allowing the RGB LED to emit the color. Also, use a ``delay()`` function to determine how long the color is displayed.


.. code-block:: Arduino
    :emphasize-lines: 8,9

    void loop() {
        // Generate random values for each color component between 0 and 255
        int redValue = random(0, 256);    // Generate a random red value
        int greenValue = random(0, 256);  // Generate a random green value
        int blueValue = random(0, 256);   // Generate a random blue value

        // Apply the random color values to the RGB LED
        setColor(redValue, greenValue, blueValue);
        delay(1000);  // Wait for 1 second
    }


6. Your complete code is now ready. You can upload it to the R3 board, and you will see the RGB LED display a random color every second.

.. code-block:: Arduino
    :emphasize-lines: 19,20

    void setup() {
        // put your setup code here, to run once:
        pinMode(9, OUTPUT);   // Set Blue pin of RGB LED as output
        pinMode(10, OUTPUT);  // Set Green pin of RGB LED as output
        pinMode(11, OUTPUT);  // Set Red pin of RGB LED as output
        
        // Initialize random seed based on an unconnected analog pin
        // This ensures a different sequence of random numbers on each reset
        randomSeed(analogRead(0));
    }

    void loop() {
        // Generate random values for each color component between 0 and 255
        int redValue = random(0, 256);    // Generate a random red value
        int greenValue = random(0, 256);  // Generate a random green value
        int blueValue = random(0, 256);   // Generate a random blue value

        // Apply the random color values to the RGB LED
        setColor(redValue, greenValue, blueValue);
        delay(1000);  // Wait for 1 second
    }

    // Function to set the color of the RGB LED
    void setColor(int red, int green, int blue) {
        // Write PWM value for red, green, and blue to the RGB LED
        analogWrite(11, red);
        analogWrite(10, green);
        analogWrite(9, blue);
    }

7. Finally, remember to save your code and tidy up your workspace.

**Summary**

By the end of this lesson, you will not only have learned about randomness in programming and how to manipulate it to create vibrant, unexpected visual displays but also appreciated the simple beauty of randomness in everyday life. Programming can be as unpredictable as life itself, and with the right tools, you can harness that unpredictability in creative and functional ways.

**Question**

What are some situations where randomness is used to solve problems in everyday life, aside from randomly picking colors for decoration and choosing lottery numbers?