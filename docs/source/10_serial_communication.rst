10. Serial Communication
================================


The Serial Monitor is an integral tool within the Arduino IDE, allowing direct communication between the R3 board and a computer. This feature is particularly useful when dealing with analog signals where visual indicators like LED brightness are insufficient to reflect detailed signal levels, unlike digital signals where the state (on or off) is evident.

In this session, you will learn how to send data and information to the Serial Monitor, enabling you to view the converted analog values from the potentiometer's voltage readings.

1. Open the previously saved sketch, ``Lesson5_Fade_LED``. Choose "Save As..." from the "File" menu, and rename it to ``Lesson5_Serial``. Click "Save".

2. To utilize the Serial Monitor, you must include a command that initiates serial communication on the R3 board. 

This command is typically placed in the ``void setup()`` section of the sketch. The command ``Serial.begin(baud)`` starts the serial communication, where ``baud`` represents the rate of data transfer per second between the computer and the R3 board. Common baud rates are 9600 and 115200 bits per second.


.. code-block:: Arduino
    :emphasize-lines: 5

    void setup() {
        pinMode(9, OUTPUT);  // Set pin 9 as output
        pinMode(10, OUTPUT); // Set pin 10 as output
        pinMode(11, OUTPUT); // Set pin 11 as output
        Serial.begin(9600);  // Serial communication setup at 9600 baud
    }

.. note::
    
    Add comments to this line, paying attention to capitalization and ensuring you include the semicolon at the end.

3. You are now ready to use the Serial Monitor to print data. You will utilize ``Serial.print()`` to display data and other texts.

Here's how to use it:


    * ``Serial.print()``: Prints data to the serial port as human-readable ASCII text. 

    **Syntax**
       - ``Serial.print(val)``
       - ``Serial.print(val, format)``

    **Parameters**
    
        - ``Serial``: serial port object.
        - ``val``: the value to print. Allowed data types: any data type.

This command can represent various data types and formats, including numbers, floating points, bytes, and strings. For example:

.. code-block:: Arduino

    Serial.print(78);                // outputs "78"
    Serial.print(78, BIN);           // outputs "1001110"
    Serial.print(1.23456);           // outputs "1.23"
    Serial.print(1.23456, 0);        // outputs "1"
    Serial.print('N');               // outputs "N"
    Serial.print("Hello world.");    // outputs "Hello world."


4. Now, in the ``void loop()``, use this command to print a prompt indicating the data about to be printed. This is helpful when differentiating multiple data prints at once.

.. code-block:: Arduino
    :emphasize-lines: 7

    void loop() {
        readValue = analogRead(A0);    // Read value from potentiometer
        writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
        analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
        analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
        analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
        Serial.print("Read Value: ");  // Prompt for the read value
    }

5. Now print the value stored in the ``readValue`` variable. To ensure each output appears on a new line in the Serial Monitor, use ``Serial.println()``, which adds a newline character at the end of the print statement.
    
    .. note::

        Note the difference in printing characters or strings (which must be enclosed in quotes) versus variables that are inserted directly.
    
    .. code-block:: Arduino
        :emphasize-lines: 8

        int readValue = 0;
        int writeValue = 0;

        void setup() {
            pinMode(9, OUTPUT);   // Set pin 9 as output
            pinMode(10, OUTPUT);  // Set pin 10 as output
            pinMode(11, OUTPUT);  // Set pin 11 as output
            Serial.begin(9600);   // Serial communication setup at 9600 baud
        }

        void loop() {
            readValue = analogRead(A0);    // Read value from potentiometer
            writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
            analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
            analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
            analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
            Serial.print("Read Value: ");  // Prompt for the read value
            Serial.println(readValue);     // Print the potentiometer value
        }

6. At this point, the code is essentially complete. Click "Upload" to upload the code to the R3 board.

7. Afterward, click on the "Serial Monitor" button in the top right corner of the Arduino IDE.

    .. image:: img/5_dimmer_led_serial.png
        :align: center

8. If you see garbled data displayed, you will need to adjust the baud rate to match the one set in your code.

    .. image:: img/5_dimmer_led_serial_baud.png
        :align: center

9. You may encounter another issue where the data refreshes too quickly to be readable. To address this, add a ``delay()`` function to slow down the main loop. Start with a delay of 100 milliseconds. You can adjust this delay later as needed.

    .. code-block:: Arduino
        :emphasize-lines: 19

        int readValue = 0;
        int writeValue = 0;

        void setup() {
            pinMode(9, OUTPUT);   // Set pin 9 as output
            pinMode(10, OUTPUT);  // Set pin 10 as output
            pinMode(11, OUTPUT);  // Set pin 11 as output
            Serial.begin(9600);   // Initialize serial communication at 9600 baud
        }

        void loop() {
            readValue = analogRead(A0);    // Read value from the potentiometer
            writeValue = readValue / 4;    // Scale readValue to fit LED brightness range
            analogWrite(9, writeValue);    // Apply brightness to LED on pin 9
            analogWrite(10, writeValue);   // Apply brightness to LED on pin 10
            analogWrite(11, writeValue);   // Apply brightness to LED on pin 11
            Serial.print("Read Value: ");  // Prompt for the read value
            Serial.println(readValue);     // Print the potentiometer value
            delay(100);                    // Wait for 0.1 seconds
        }

10. Once you re-upload the code, the printed data will be clearer. Now, as you turn the potentiometer, you'll see the values displayed in the Serial Monitor increase, resulting in brighter LEDs; smaller values will dim the LEDs.

    .. note::

        Whenever data is transmitted from the board to the computer, you should see the TX LED on your R3 board flashing.

11. You can continue to explore features of the Serial Monitor, such as toggling auto-scroll, enabling timestamps, and customizing output, which can enhance your data viewing experience.

    .. image:: img/5_dimmer_led_serial_tool.png
        :align: center

12. Finally, remember to save your code and tidy up your workspace.


**Summary**

In this lesson, we learned about the origins of communication, how to initialize the serial monitor in the code, how to use commands to print strings and data, and how to view them in the Serial Monitor. With this serial monitor tool, we can monitor data states in real-time, which can be very beneficial for our projects.

**Question**:

We've only printed the variable ``readValue``. How would you modify the code to print both ``readValue`` and ``writeValue`` simultaneously? Write the additional code in your handbook and verify it through the Arduino IDE.
