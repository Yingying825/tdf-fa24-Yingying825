# Week9: Progress Report

### **Week of 10/26/2024**

I followed TJ’s amazing tutorial and have finished the four gpt experiments as showing below.

<img width="800" alt="gpt experiment_01_number slider" src="assets/gpt_experiment_01_number_slider.png"> 

I first played with number slider to see the results it effects.

<img width="400" alt="gpt experiment_01_greeting text" src="assets/gpt_experiment_01_greeting_text.png"><img width="400" alt="gpt gpt experiment_01_greeting text02" src="assets/gpt_experiment_01_greeting_text02.png">

And then, I added the greeting text to the demo page, which is really fun to do.

<img width="400" alt="gpt+ instruct experiment_01_prompt" src="assets/gpt_instruct_experiment_01_prompt.png"><img width="400" alt="gpt_instruct_experiment_01_prompt02" src="assets/gpt_instruct_experiment_01_prompt02.png"> 

I also tried to write some prompts by following TJ’s steps.

<img width="800" alt="gpt_instruct_experiment_01_knowledge" src="assets/gpt_instruct_experiment_01_knowledge.png">

It’s also interesting to see that we can add our own knowledge data base into this small LLM. I will definitely experiment it by adding other information later on.  

<img width="300" alt="gpt_instruct_rag_experiment_01_prompt" src="assets/gpt_instruct_rag_experiment_01_prompt.png"><img width="300" alt="gpt_instruct_rag_experiment_01_prompt02" src="assets/gpt_instruct_rag_experiment_01_prompt02.png"><img width="300" alt="gpt_instruct_rag_experiment_01_prompt03" src="assets/gpt_instruct_rag_experiment_01_prompt03.png">

By trying to add the instruction into the prompt, it’s so exciting to see the machine follows my instruction exactly. 

<img width="800" alt="gpt_instruct_rag_variable_experiment_01" src="assets/gpt_instruct_rag_variable_experiment_01.png">

After adding two variables, and posing onto postman, it works perfectly!




# Week8: Progress Report

### **Week of 10/19/2024**

I figured out the particle team working flow that user needs to add product into the group by themselves. 

<img width="400" alt="Group_Device" src="assets/Group_Device.png"> <img width="400" alt="Group_Device2" src="assets/Group_Device2.png">

I figured out the particle cloud communication between devices with Dianer by dividing devices into publisher and subscriber. When user press the button, sending “button press” messages on cloud and triggering the led, vibrator and google map locations. 

During the process, we had a hard time figuring out the mechanism of group communication, but we ended up going back to the right track after several hours exploration. We figured out our final mutual functioning ecosystem.

I got the accelerometer data, access token from Particle Cloud, and I can also got the data through my computer terminal, in order to train the machine learning model. But we decided to use the specific range of data changes as an indicator of sudden fall at this stage. 

<img width="400" alt="Accel" src="assets/Accel.png"> <img width="400" alt="Accel_data" src="assets/Accel_data.png"> <img width="400" alt="Accel_terminal" src="assets/Accel_terminal.png">

After making everything work on the breadboard, I successfully soldered one of the prototype boards to make the circuit more stable. I also connected Accelerometer with Photon2 with outside Lipo battery to make the product work without connecting with computer. 

<img width="400" alt="prototype board" src="assets/prototype board.jpg">

After finishing the whole ecosystem, we shoot the video according to the script and I got the artificial intelligence audio that fits into the scripts and we finally finish editing the video.

video link: https://youtu.be/-pfiwCFtWow







# Week7: Progress Report

### **Week of 10/12/2024**

I successfully got my location data by using Google Maps API.

<img width="800" alt="location_data" src="assets/location_data.png">

got the google map geolocation api key first

key=API_KEY

AIzaSyBv39OIes73QOFWcOIXVTBKi12OYXrTIz0

and then, went to the particle ide to run the google maps firmware library on the device

include <google-maps-device-locator.h>;

compiled and flashed successfully
but couldn’t see the data because of a configuration error

went to the console — integrations — google maps device locator and pasted my api key;

<img width="800" alt="flash_location" src="assets/flash_location.png">

Another error showed up but went to the link website and enabled my api key, which I didn’t fully enable it before.

For the other functionalities, I also tried to figure out the accelerometer differences between **LIS3DH and MPU6050.** And we decided to stick with what we have now, which is MPU6050. We need to do the edge impulse for machine learning the user behavior. 

****And then we broke down the function into different tasks to test them separately. I am dealing with the **Interaction Modes with Button Presses.** The ideal result we want to achieve is: 
Press the button once, the led blink green once;

Press the button for two times, the led blink yellow for two times and the device keep sharing the real-time location;
Press the button for over three times, the led keep blinking red and the device keep sharing the real-time location;

Keep pressing the button to turn off the led and stop sharing the location.

<img width="800" alt="buttonpressled" src="assets/buttonpressled.png">

I experimented with the code for a long time by trying interrupt and debouncing, and I still could not complete the long-press function. We ended up synchronizing the light with vibrator by pressing the button at the same time and control the blinking and vibration times. 

<img width="800" alt="synchronize" src="assets/synchronize.jpg">


# Week6: Progress Report

### **Week of 10/05/2024**

At first, I soldered shied and put on the Photon2. And then, I tried to connect them with my computer using usb cable. But there’s a yellow light blink once at the CHG port and i tried to debug the problem for a long time.

<img width="400" alt="Soldering" src="assets/Soldering.jpg">

**MPU6050 sensor:**

<img width="800" alt="MPU_Flash" src="assets/MPU_Flash.png">

I tried to enable function: accelgyro.getAcceleration(&ax, &ay, &az) and got the data. I compared the acceleration data with the motion data.

<img width="400" alt="MPU_Circuit" src="assets/MPU_Circuit.jpg">

<img width="800" alt="MPU_Motion_Result" src="assets/MPU_Motion_Result.png">

<img width="800" alt="MPU_Accleration_Result" src="assets/MPU_Accleration_Result.png">

**APDS-9960** sensor, which is an integrated module capable of **gesture recognition**, **proximity detection**, **ambient light sensing**, and **RGB color sensing**.

methods for enabling different sensors (`enableGestureSensor(true)`, `enableLightSensor(false)`, `enableProximitySensor(false)`) 

I was wondering why enable the light sensor and the proximity sensor by using (false) not the same one as the gesture sensor (true)

The **parameter (`true` or `false`)** in the methods controls whether the corresponding sensor should use **interrupts** or **polling.**

- **`true`**: Enables **interrupt mode**.
- **`false`**: Enables **polling mode**.
- **Interrupt Mode (`true`)**:
    - **Gesture Sensor** is enabled with `true` in `enableGestureSensor(true)`.
    - When a sensor is set to use interrupts, the sensor itself will generate an interrupt signal whenever an event of interest occurs (e.g., a gesture is detected).
    - This means the **microcontroller doesn’t need to continuously check the sensor's status**, freeing it up to perform other tasks and reducing power consumption. It will only respond when an event occurs, such as a gesture being detected.
- **Polling Mode (`false`)**:
    - The **Light Sensor** and **Proximity Sensor** are enabled with `false` in `enableLightSensor(false)` and `enableProximitySensor(false)`.
    - In **polling mode**, the code continuously checks (or "polls") the sensor to see if any new data is available. This is a simpler approach and is often used when you want to read the sensor at regular intervals rather than waiting for a specific event to trigger an action.
    - Polling is more straightforward to implement but can be less efficient since the microcontroller must repeatedly ask the sensor for data rather than being alerted only when needed.

**`if ( !apds.setProximityGain(PGAIN_2X) ) {`**
The **`!`** in `if ( !apds.setProximityGain(PGAIN_2X) )` means "not," which indicates that if the return value of `setProximityGain()` is `false` (indicating failure), then the code inside the `if` block will execute.

**`PGAIN_2X`** is an argument that defines the proximity gain level. The gain determines how sensitive the sensor is to objects that are nearby.

<img width="400" alt="APDS_Circuit" src="assets/APDS_Circuit.jpg">

<img width="800" alt="APDS_Proximity_Result" src="assets/APDS_Proximity_Result.png">

And then, I explored the gesture sensor function and Light sensor function by altering the code.

<img width="800" alt="APDS_Gesture_Flash" src="assets/APDS_Gesture_Flash.png">

<img width="800" alt="APDS_Gesture_Result" src="assets/APDS_Gesture_Result.png">

I also tried and alterd the code for the light sensor.

<img width="800" alt="APDS_Light_Result" src="assets/APDS_Light_Result.png">

This is the diagram showing the whole exploration. 

<img width="800" alt="data_diagram" src="assets/data_diagram.png">

After the exploration, I’m thinking about using these two sensors in the transportation system. The MPU 6050 sensor to monitor vehicle dynamics, such as sudden acceleration, sharp turns or braking and also enhance passenger safety like track bus stability and detect unsafe driving.
For the APDS 9960 sensor, it can be used for touchless controls like requesting stop or opening doors via gestures. In addition, it can control seat lights when passengers are nearby by using proximity-based lighting.

For the group proposal, this is the link: 
https://docs.google.com/document/d/1NTrjd6Ivd9DsqQrRy5k4kXpfnqgkJmYc25LHgkNxIuk/edit?usp=sharing




# Week5A: Progress Report

### **Week of 09/30/2024**

Firstly, i tried to connect the photon2 with my home wifi. I logged in Particle website and configure wifi panel to connect with my wifi. 

I started with the file **03_altering_periodicity**; 

Cause i did not use any c languages before and I started to learn the meaning behind the code with the help of Chatgpt. 

<img width="800" alt="01Process" src="assets/09_29Homework_01Process.png">

I learned about 

- **`char hello[] = "Hello World!";`**
- **`char`** is a data type used to store **a single character** (e.g., letters, digits, symbols).
- **`hello`** is the **name** of the character array that you are declaring.
- The **empty brackets (`[]`)** indicate that the size of the array will be determined automatically based on the length of the string assigned to it.
- **`"Hello World!"`** is a **string literal** assigned to the character array **`hello`**.

**Memory Representation**

The array `hello` will look like this in memory:

```

| H | e | l | l | o |   | W | o | r | l | d | ! | \0 |
```

- The **`\0`** is the null terminator added automatically to signify the end of the string.
- The total length of this character array is **13** (**`12`** characters for **`"Hello World!"`** + **`1`** null terminator).

- **`pin_t button_in = D2;`** is declaring a **variable** that represents a pin.
- **`pin_t`** is a **data type** that is used to represent a **pin** on the microcontroller.
- **`button_in`** is the **name of the variable** that you are declaring.
- **`D2`** is the **identifier** for **Digital Pin 2** on the microcontroller board.

- **`int`**: A variable type used to store whole numbers (e.g., -10, 0, 42).
- **`bool`**: A variable type used to store a logical value, either **`true`** or **`false`**.

- **`void button_press(void);`:** learned about the use of Function Prototype, which can be called from anywhere in the code.
- **`;` (semicolon)**: indicates that this line is a **declaration** only, not a definition.
- the **definition** (**`void button_press(void) { ... }`**) provides the actual implementation.

- **`interrupts();`** explicitly **enables global interrupts**. Interrupts are **not functions themselves**, but they trigger functions (ISRs) when specific events occur.

- **`pinMode(button_in, INPUT_PULLDOWN);`** sets the **mode** of a specific **pin** called **`button_in`.**
- **`INPUT_PULLDOWN`**: This configures the pin as an **input** and also **activates an internal pull-down resistor**. Internal down resistor ensures that when the button is not pressed, the pin reads **LOW** (0V), avoiding floating values (undefined states).

- **`attachInterrupt(button_in, button_press, RISING);`** sets up an interrupt on the **`button_in`** pin that calls the **`button_press()`** function whenever the button goes from unpressed (LOW) to pressed (HIGH).
- **`attachInterrupt()`** is used to **attach an interrupt** to a specific pin, meaning that the microcontroller will trigger an interrupt service routine when a specified event occurs on that pin.
- **`button_press`**: The name of the **function** that will be called when the interrupt occurs. This is called an **interrupt service routine (ISR)**.
- **`RISING`** means the interrupt will trigger when the signal on the pin goes from **LOW to HIGH**, indicating a rising edge (typically when a button is pressed).

- **`Log.info()`** is used for **logging** messages, and it works similarly to **`Serial.print()`** in the Arduino environment. It outputs information, typically for debugging purposes.

I found out the logic behind it is similar to Arduino with python but the writing of coding is totally different and it’s so hard for me to remember.

**Compiled & Flashed & Printed Successfully**

<img width="800" alt="01Compile" src="assets/09_29Homework_01Compile.png">

<img width="800" alt="01Flash" src="assets/09_29Homework_01Flash.png">

<img width="800" alt="01Result" src="assets/09_29Homework_01Result.png">

<img width="400" alt="Button" src="assets/Button.jpg"><img width="400" alt="Button_Pressed" src="assets/Button_Pressed.jpg">

For the first time, I changed the sentence “Hello World!” into “Goodnight World!”:
char night[] = "Goodnight World!";

<img width="800" alt="01Compileb" src="assets/09_29Homework_01Compileb.png">

I also change the name here:
Log.info("current character: %c", night[count]); 

I encountered a problem when i used save as the file, it gave me an error when i was trying to compile and flash. I opened a new project and rewrite the code, the error disappeared. 

For the **04 Make it blink file**:

I first questioned about the differences between pin_t button_in = D2; and const pin_t button_in = D2:

- **`const`** is recommended for **pin assignments** like **`button_in`** if do not need to change the pin during runtime.

I questioned about the sequences of following:

- **`bool button_pressed = false;`** is declared before the **function prototype** to ensure that **`button_pressed`** is known to all functions that need to use it.

- const pin_t led_out = D7; pinMode(led_out, OUTPUT); digitalWrite(led_out, HIGH);
- **`OUTPUT`** is a **constant** that indicates that the pin should be used as an **output pin**.
- Setting a pin as **OUTPUT** means the microcontroller will be able to set the pin voltage **HIGH** (e.g., 3.3V or 5V) or **LOW**(0V) depending on the state you want.

**Compiled & Flashed & Button Pressed Successfully**

<img width="800" alt="02Compile" src="assets/09_29Homework_02Compile.png">

<img width="800" alt="02Flash" src="assets/09_29Homework_02Flash.png">

<img width="800" alt="02ButtonResult" src="assets/09_29Homework_02ButtonResult.png">

<img width="400" alt="Green_Blink_red" src="assets/Green_Blink_red.jpg">

For the changes, I decided to add another button to change the led behavior.

<img width="800" alt="02Flashb" src="assets/09_29Homework_02Flashb.png">

I added second button pin definition**,** Added bool button2_pressed = false; updated setup by adding pinMode and attachInterrupt. Added a new function button2_press(); 

I was also changing the Log.info, it appeared an error showing "Log" is ambiguousC/C++(266). And chatgpt helped me to solve the issue by adding Particle::
Finally, I changed the code in loop to change LED behavior.
I experimented with the circuit and made it showing button pressed.

For the **05 Make it blink outside file**:

I spent some time fixing the circuit problem and finally turned on the green light. Because of the transportation system i wrote down in my report, i decided to add another red light to mimic the traffic light. But the red light is not that vivid compared to the green and i decided to turn them on at different times to reduce the load on the power supply.

<img width="800" alt="03Compile" src="assets/09_29Homework_03Compile.png">

<img width="800" alt="03Flash" src="assets/09_29Homework_03Flash.png">

<img width="400" alt="Grlight_plus_Rdlight" src="assets/Grlight_plus_Rdlight.jpg">

I changed loop function to alternate between turning green light and red light. But it didn’t help for the red light but the blue light with green light works well. 

<img width="800" alt="03Flashb" src="assets/09_29Homework_03Flash.png">

<img width="400" alt="Green_Blink_red" src="assets/Green_Blink_red.jpg"> <img width="400" alt="Internal_Light" src="assets/Internal_Light.jpg">

**How These Elements Form a Cohesive Whole**

The timing system, button interrupts, and cloud publishing all work together to create a system that’s responsive, informative, and remotely accessible.

Adding components like additional LEDs and buttons made the system more complex, but they also showed how embedded systems can handle multiple sources of input while still maintaining core behavior. It showed that an embedded system can have many entry points for user interaction (buttons) and output feedback mechanisms (LEDs, logs, cloud publishing).

**Potential Applications and Advantages**

A system like this can be used in wearable technology or smart home systems, where buttons, LEDs, and cloud connectivity could form a user-friendly interface.

The advantages i think are scalability, cloud connectivity and real-time interaction. It’s easy to add more sensors, outputs, or buttons to form the whole line. Publishing messages to the Particle cloud allows for remote monitoring and control, which can be suited for smart home systems. The use of interrupts for the buttons ensures that user input is handled immediately, which is crucial for designing responsive interfaces.

**Missing Ecosystems in Daily Life**

A key realization is that real-time response systems are underused in everyday consumer products. Systems that can adapt in real-time based on user input or environmental data could be more widely implemented in things like healthcare devices or consumer electronics. Cloud integration with physical systems is also lacking in many household products, which could be improved by integrating cloud monitoring and control.

**Relation to Other Systems**

In my demo, buttons were used to trigger actions, similar to stop request buttons in public transport, while the Particle Cloud was utilized for publishing events, just like GPS-based real-time tracking in transit systems. Serial logs allowed centralized monitoring, similar to tracking vehicles and schedules in public transportation. The periodicity feature that adjusted LED blink rates parallels how bus schedules change dynamically based on demand. Visual feedback from LEDs after button presses is comparable to bus stop buttons lighting up to confirm requests. These IoT elements—buttons, LEDs, cloud, and timing—demonstrate how real-time interaction, monitoring, and automation can create efficient systems, similar to public transit.

# Week5B: Progress ReportB

### **Week of 10/02/2024**

I tried one more example from the weekend’s folder. **I started with the file 06_publishing_info;** 
**`snprintf()`**: This function is used to convert the integer **`count_cycles`** into a string and store it in **`count_cycles_str`**.

This array is then used for publishing data to the cloud since functions like **`Particle.publish()`** require the data to be in string form.

<img width="800" alt="04Compile" src="assets/10_02Homework_04Compile.png">

<img width="800" alt="04Flash" src="assets/10_02Homework_04Flash.png">

I checked Particle cloud and i saw the number of my cycles. 

<img width="800" alt="04Cloud" src="assets/10_02Homework_04Cloud.png">

For the revision requirement, I decided to add a restriction for publishing. I would like to make the publish only if the cycle count is a multiple of 5. 

<img width="800" alt="04bCloud" src="assets/10_02Homework_04bCloud.png">

**Next, I started to work on the fsr (force sensitive resistor) -> RGB-led color fader**

int rValue = 0;
int gValue = 0;
int bValue = 0;

- **`rValue`, `gValue`, `bValue`** are used to control and adjust the intensity of each color component of the RGB LED. By modifying these values, i can control the brightness and color mix of the RGB LED.
- **`analogRead()`** is a function that reads the voltage level on the specified analog pin (**`FSRPIN`**).

During the coding process, I got confused about why we need to set both target and color, not only colors. And I figured it out that by setting up both can make the led transition much smoother. And when i first typed in codes, there was an error show up saying 'setTarget' was not declared in this scope either the “setColor”. I added function prototype before the setup and solved the problem.

<img width="800" alt="01Compile" src="assets/10_02Homework_01Compile.png">

<img width="800" alt="01Flash" src="assets/10_02Homework_01Flash.png">

<img width="300" alt="RDlight" src="assets/10_02Homework_RDlight.jpeg"><img width="300" alt="GRlight" src="assets/10_02Homework_GRlight.jpeg"><img width="300" alt="BLlight" src="assets/10_02Homework_BLlight.jpeg">

**basic button send-on-change example**

- const char *be = "button_event"; // Name of published event
**`be`** is the **event name** used when publishing button presses to the Particle cloud.
- **`volatile int state`** and **`volatile int state_was`** are used to track the **current state** and **previous state** of the button.

- **`state = digitalRead(button)`**: Reads the **button state** (either **HIGH** or **LOW**).
- **`digitalWrite(ledpin, state)`**: Turns the **LED on or off** depending on the button state.

- String state_str = String(state); // Convert button state to string;

I was wondering about why we need to covert state to string, and after consulting with chat gpt, I understood that it can make it easier to send or publish the button state to the cloud or use it for text-based operations.

<img width="800" alt="02compile" src="assets/10_02Homework_02compile.png">

<img width="800" alt="02Flash" src="assets/10_02Homework_02Flash.png">

<img width="800" alt="02Cloud" src="assets/10_02Homework_02Cloud.png">

<img width="400" alt="02Circuit" src="assets/10_02Homework_02Circuit.jpg">

**potentiometer -> oled display**

#define POT_PIN A0 // Potentiometer is connected to A0

- I am wondering why we need to connect it to A0 not D2,D3, or D7, and I asked chat gpt:
On the Particle Photon (and most microcontrollers), **`A0`, `A1`, `A2`**, etc., are **analog input pins**.
- When connect the potentiometer to **`A0`**, we can read the **exact voltage level** as a **digital number**, which represents the position of the potentiometer.
- **Digital pins** like **`D2`, `D3`, `D7`**, etc., are designed for **digital input/output**.
- Digital pins can only read **two states**: **HIGH** or **LOW**.
    - **HIGH** typically means 3.3V (or 5V depending on the microcontroller).
    - **LOW** means 0V.
- Using **`A0`** allows you to read the potentiometer value accurately and utilize it for whatever function you need, such as **adjusting brightness**, **volume**, or other variables in your project.

During the compile process, I encountered compile problem and Dianer helped me to solve the library hierarchy problems.
By dragging around the file, chatgpt suggests me to clean the file in particle benwork panel. So i cleaned the file first and compiled them later. 

<img width="800" alt="03Clean" src="assets/10_03Homework_03Clean.png">

<img width="800" alt="03Compile" src="assets/10_03Homework_03Compile.png">

<img width="800" alt="03Flash" src="assets/10_03Homework_03Flash.png">

<img width="800" alt="03Output" src="assets/10_03Homework_03Output.png">

<img width="400" alt="03Circuit" src="assets/10_03Homework_03Circuit.jpg">

The prior examples have simple interaction and the demo projects have various input. The similarities are they all have certain kind of visual feedback and have simple physical inputs. By adding a motion sensor may be more equivalent to my life, so i can have a night lamp during night time. I think machine learning can help to smart tracking the volume of traffic in order to adjust the lines and lights efficiently. If combining the examples into larger ecosystem, i may think about smart home system, acts as a personal home assistant.








# Week4: Progress Report

### **Week of 09/19/2024**

**Diagram**:

<img width="800" alt="map" src="assets/map.png">

**Brief Explanation:**

Diagram Explanation: 

I chose the Transportation & Mobility Ecosystem because I use public transportation every day.

The ecosystem revolves around my smartphone, which connects to transit apps for real-time schedule updates, payment systems and transportation networks.

Information Flow: Data flows from transit systems to the apps on my phone, providing live updates about schedules and traffic conditions. My GPS location also helps the apps recommend the best routes.

Feedback Loops: Real-time updates influence my choices, like taking alternative routes when delays occur. Over time, apps use my travel history to provide better suggestions, while contactless payments track my usage, offering rewards system.

**Personal Performance Reflection:**

Introduction to New Tools and Technologies:

This week, I started using Postman, a platform for API testing, and Photon, a tool for physical computing. Both are expanding my technical capabilities and project possibilities.

Hands-on Experience in the Woodshop:

I also used a woodshop saw to cut wood, gaining practical experience in material manipulation and understanding safety and precision in woodworking.
Accidentally found a human face too.


<img width="500" alt="face" src="assets/face.jpg">

**Challenges and Learnings:**

Working with the woodshop saw was challenging due to the need for precise measurements and adherence to safety protocols. This experience enhanced my practical skills with wood as a material.

**Reflection and Future Directions:**

By exploring both digital and physical tools, I plan to further develop my skills with Postman and Photon, and continue improving in hand-on working. These skills will help in integrating software with physical computing for future technology-driven projects.




# Week3: Progress Report

### **Week of 09/12/2024**

**Exploring Advanced Design Techniques:**

<img width="500" alt="voronoi" src="assets/voronoi.jpg">

This week, I expanded my technical skills by learning how to use Voronoi diagrams within Rhino Grasshopper. This technique allowed me to create more complex and visually appealing designs, which adds a new dimension to my work. 

**Experimenting with Resin Printing:**

<img width="500" alt="resin_wash" src="assets/resin_wash.jpg">

I conducted my first trial with resin printing myself, which was an exciting, albeit time-consuming, process. Despite the challenges, mastering this technique was rewarding. The hands-on experience also taught me about the different physical properties of various resin materials. The resin I chose required multiple washes post-printing, adding to the complexity but enhancing the final product's quality.

**Utilizing Markforged Machine:**

<img width="500" alt="markforged" src="assets/markforged.jpg">

Additionally, I experimented with the Markforged machine to print using carbon fiber nylon filament. This was particularly intriguing as it introduced me to the capabilities and potential of printing with reinforced materials, which could be crucial for future robust design applications.

**Challenges with 3D Printing Accuracy:**

One of the setbacks this week was my attempt to model and print a 3D hinge with the box together. Unfortunately, the print failed due to issues with printing accuracy. This has highlighted the need for further experiments to refine the process and achieve the desired precision.

**Ongoing Projects and Plans:**

<img width="500" alt="box_lid" src="assets/box_lid.jpg">

Amidst these experiments, I am still in the process of finalizing the perfect packaging solution for my jewelry brand. This remains a critical component of my project, as the packaging must not only be protective but also reflect the aesthetic and quality of the jewelry inside.





# Week2: Progress Report

### **Week of 09/12/2024**

Following the tutorial, I practiced basic Rhino modeling before experimenting with the Grasshopper file for a phone stand. 

<img width="500" alt="rhino1" src="assets/rhino1.jpeg">

I managed to modify the parameters and "baked" a new model by experimenting with the phone stand file. The process helped me understand the underlying logic of parametric design. 

<img width="500" alt="rhino2" src="assets/rhino2.png">

<img width="500" alt="gh1" src="assets/gh1.png">

<img width="500" alt="gh2" src="assets/gh2.png">

I then drew a diagram illustrating the logic flow behind the phone stand, which clarified the process.

<img width="500" alt="diagram" src="assets/diagram.png">

In addition, I also followed another youtube tutorial and made a parametric box by using Grasshopper. It solidifies my understanding of parametric design and the logic flow behind it.

<img width="500" alt="parametric_box" src="assets/parametric_box.png">



# Week1: Progress Report

### **Week of 08/26/2024**

### **Reflections**

**What I Learned:**

This week, I focused on learning the basics of the Kuka KR 6 R900-2 Agilus Robots, nicknamed Lucy and Ethel at jacobs. I explored their mechanical and software interfaces, essential for precise automation tasks.

**How I Learned It:**

My learning involved hands-on workshops and peer discussions, which helped me understand the robots' capabilities and limitations.

**Assessment of Work:**

My work with the robots is at a beginner stage. I've controlled the arm to do basic task and am exploring more complex operations.

**Challenges Encountered:**

I tried using a robotic arm to draw my jewelry brand's logo. The result was slightly off due to the pen's tip not being fine enough for detailed line designs.

<img width="300" alt="Kuka" src="assets/Kuka.jpeg">

**Future Directions:**

This experience has shown the importance of matching the right tools with robotic systems for precision tasks. It will guide my future projects requiring precise robotic interactions.

**Speculations**

**Future Direction for the Tools:**

I believe modifying a robotic arm to include a 3D printer extruder could allow printing on uneven surfaces, transforming how we use 3D printing in today’s manufacturing.

**Future Direction for the Work:**

Using the Omax Waterjet Cutter has inspired me to pursue designs that were previously too complex due to material constraints, thanks to its precise cutting capabilities.

<img width="300" alt="Jet" src="assets/Jet.jpeg">





# Hello DES INV 202 Student!
Welcome to your new GitHub repository! 

# Outline
[week 1](README.md#week-1-example-report-1)

week 2, etc...

---

# Github Background Information & Context
If you’re new to GitHub, you can think of this as a shared file space (like a Google Drive folder, or a like a USB drive that’s hosted online.) 

This is your space to store project files, videos, PDFs, notes, images, etc., and (hopefully, neatly) organize so it's easy for viewers (and you!) to navigate. That said, it’s super easy for you to share any file or folder with us (your TDF instructional team) - just send us the link!  As a start, feel free to simply add images to the `/assets` folder, which is located [here](/assets). 

The specific file that I’m typing into right now is the **README.md** for this repo. 
##### (💡 TIP: The .md indicates that we’re using [Markdown formatting.](https://www.markdownguide.org/cheat-sheet/)) #####
<h6> (💡 TIP 2: GitHub Markdown supports <a href="https://gist.github.com/seanh/13a93686bf4c2cb16e658b3cf96807f2"> <em>HTML formatting</em> too, including emojis 😄</a>, in case that helps!) </h6>

### :star: Whatever you write in your **README.md** will show up on the “front page” of your GitHub repo. This is where we’ll be looking for your [weekly progress reports](https://github.com/Berkeley-MDes/24f-desinv-202/wiki/3.0-Weekly-Submissions#weekly-progress-report). They might look something like this: ###

# Week 1: Example Report 1 #
## Week of 09/05/2024

This week, I designed a cool phone stand made of rocks. Check out all my cool sketches and progress photos from this week below, etc., etc....

<img width="200" alt="Cool Phone Stand made of rocks" src="assets/exampleimg.png">

---

It's time to start making this space your own! If you want to save these instructions, make a copy.  Also, feel empowered to delete everything in this README.md and start documenting! 

Excited to work with you,
your TDF teaching team

PS: let us know if you have any questions!!

PPS: 

## Quick Links, compiled here for your convenience: ##

- [TDF Wiki](https://github.com/Berkeley-MDes/24f-desinv-202/wiki) - the ultimate source for truth and information about the course and assignments
- [Google Drive Folder](https://drive.google.com/drive/u/0/folders/1DJ1b6sSDwHXX6NRcQYt10ivyQSgU0ND6) - slides and other resources
- [bCourses](https://bcourses.berkeley.edu/courses/1537533) - where the grading happens
