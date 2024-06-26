M5StickC
========

The M5StickC is a portable, easy-to-use, tiny but mighty IoT development device.

Here you will find an example of how to use the M5StickC node in IoTempower.

Example
-------

Configure the ``node.conf`` file:

..  code-block:: bash
  
  board="m5stickc"

Configure the ``setup.cpp`` file:

..  code-block:: cpp

    out(led, ONBOARDLED).inverted().off(); // initialize the onboard LED
    
    button(home, BUTTON_HOME, "pressed", "released").inverted().debounce(10);
    
    button(buttom, BUTTON_RIGHT, "pressed", "released").inverted().debounce(10);
    
    m5stickc_display(console, 1, 270); // initialize LCD display as 'console'

    const char* id="01";
    void start() { 
        do_later(100, [] () { 
                IN(console).print("This is: stick-")
                .print(id);});} // print device id on LCD display (console)


**Note**:

- The ``inverted()`` method inverts the button logic.
- The ``debounce()`` method debounces the button.
- The ``m5stickc_display()`` method initializes the LCD display.
- The ``do_later()`` method prints the device id on the LCD display.
 
  - Helps keep track of multiple m5StickC devices.

- Change the **LCD display** color by sending an **MQTT** message to ``console``:
 
  - To adjust **background** color, use ``&&bg`` followed by a ``HEX color code``.
  - To adjust **foreground** color, use ``&&fg`` followed by a ``HEX color code``.
  
  - For example:  
   
    - Send: ``&&bg 000000`` to set the **background** to black: 
    
    ``mqtt_send your_m5_node/console &&bg 000000``
    
    - Send: ``&&fg ffffff`` to set the **foreground** to white: 
    
    ``mqtt_send your_m5_node/console &&fg ffffff``


Power switch operation:
-----------------------

- Turn it on/off
  
  - Power ``ON`` :Press power button for 2 seconds
  - Power ``OFF`` :Press power button for 6 seconds

- Charging:
 
  - The ``VBUS_VIN`` and ``VBUS_USB`` have a limited input range between ``4.8-5.5V``.
  - The ``AXP192`` power manager charges the battery from a powered ``VBUS``.

**Note:**

Supported baud rates: ``1200 ~115200, 250K, 500K, 750K, 1500K``



Features
--------


.. table::
   :widths: auto

   +----------------------+--------------------------------------------------+
   | Resources            | Parameter                                        |
   +======================+==================================================+
   | ESP32                | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi   |
   +----------------------+--------------------------------------------------+
   | Flash Memory         | 4MB                                              |
   +----------------------+--------------------------------------------------+
   | Power Input          | 5V @ 500mA                                       |
   +----------------------+--------------------------------------------------+
   | Port                 | TypeC x 1, GROVE (I2C+I/0+UART) x 1              |
   +----------------------+--------------------------------------------------+
   | LCD screen           | 0.96 inch, 80*160 Colorful TFT LCD, ST7735S      |
   +----------------------+--------------------------------------------------+
   | Button               | Custom button x 2                                |
   +----------------------+--------------------------------------------------+
   | LED                  | RED LED                                          |
   +----------------------+--------------------------------------------------+
   | MEMS                 | MPU6886                                          |
   +----------------------+--------------------------------------------------+
   | IR                   | Infrared transmission                            |
   +----------------------+--------------------------------------------------+
   | MIC                  | SPM1423                                          |
   +----------------------+--------------------------------------------------+
   | RTC                  | BM8563                                           |
   +----------------------+--------------------------------------------------+
   | PMU                  | AXP192                                           |
   +----------------------+--------------------------------------------------+
   | Battery              | 95 mAh @ 3.7V                                    |
   +----------------------+--------------------------------------------------+
   | Antenna              | 2.4G 3D Antenna                                  |
   +----------------------+--------------------------------------------------+
   | PIN port             | G0, G26, G36                                     |
   +----------------------+--------------------------------------------------+
   | Operating Temperature| 0°C to 60°C                                      |
   +----------------------+--------------------------------------------------+
   | Net weight           | 15.1g                                            |
   +----------------------+--------------------------------------------------+
   | Gross weight         | 33g                                              |
   +----------------------+--------------------------------------------------+
   | Product Size         | 48.2*25.5*13.7mm                                 |
   +----------------------+--------------------------------------------------+
   | Package Size         | 55*55*20mm                                       |
   +----------------------+--------------------------------------------------+
   | Case Material        | Plastic (PC)                                     |
   +----------------------+--------------------------------------------------+


Resources
---------

Product page:
    https://shop.m5stack.com/products/stick-c?variant=43982750843137