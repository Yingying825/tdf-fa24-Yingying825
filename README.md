# Week5: Progress Report

### **Week of 09/21/2024**

Firstly, i tried to connect the photon2 with my home wifi. I logged in Particle website and configure wifi panel to connect with my wifi. 

I started with the file 03_altering_periodicity; 

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

<img width="350" alt="Button" src="assets/Button.jpg">   <img width="350" alt="Button_Pressed" src="assets/Button_Pressed.jpg">

For the first time, I changed the sentence “Hello World!” into “Goodnight World!”:
char night[] = "Goodnight World!";

<img width="800" alt="01Compileb" src="assets/09_29Homework_01Compileb.png">

I also change the name here:
Log.info("current character: %c", night[count]); 

I encountered a problem when i used save as the file, it gave me an error when i was trying to compile and flash. I opened a new project and rewrite the code, the error disappeared. 

For the 04 Make it blink file:

I first questioned about the differences between pin_t button_in = D2; and const pin_t button_in = D2:

- **`const`** is recommended for **pin assignments** like **`button_in`** if do not need to change the pin during runtime.

I questioned about the sequences of following:

- **`bool button_pressed = false;`** is declared before the **function prototype** to ensure that **`button_pressed`** is known to all functions that need to use it.

- const pin_t led_out = D7; pinMode(led_out, OUTPUT); digitalWrite(led_out, HIGH);
- **`OUTPUT`** is a **constant** that indicates that the pin should be used as an **output pin**.
- Setting a pin as **OUTPUT** means the microcontroller will be able to set the pin voltage **HIGH** (e.g., 3.3V or 5V) or **LOW**(0V) depending on the state you want.

**Compiled & Flashed & Button Pressed Successfully**

![09_29Homework_02Compile.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_02Compile.png)

![09_29Homework_02Flash.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_02Flash.png)

![09_29Homework_02ButtonResult.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_02ButtonResult.png)

![Green_Blink_red.JPG](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/Green_Blink_red.jpg)

For the changes, I decided to add another button to change the led behavior.

![09_29Homework_02Flashb.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_02Flashb.png)

I added second button pin definition**,** Added bool button2_pressed = false; updated setup by adding pinMode and attachInterrupt. Added a new function button2_press(); 

I was also changing the Log.info, it appeared an error showing "Log" is ambiguousC/C++(266). And chatgpt helped me to solve the issue by adding Particle::
Finally, I changed the code in loop to change LED behavior.
I experimented with the circuit and made it showing button pressed.

For the 05 Make it blink outside file:

I spent some time fixing the circuit problem and finally turned on the green light. Because of the transportation system i wrote down in my report, i decided to add another red light to mimic the traffic light. But the red light is not that vivid compared to the green and i decided to turn them on at different times to reduce the load on the power supply.

![09_29Homework_03Compile.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_03Compile.png)

![09_29Homework_03Flash.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_03Flash.png)

![Grlight_plus_Rdlight.JPG](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/Grlight_plus_Rdlight.jpg)

I changed loop function to alternate between turning green light and red light. But it didn’t help for the red light but the blue light with green light works well. 

![09_29Homework_03Flashb.png](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/09_29Homework_03Flashb.png)

![Green_Blink_red.JPG](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/Green_Blink_red%201.jpg)

![Internal_Light.JPG](Week5%20Progress%20Report%20111933af310c80a38221cb4812cb4e56/Internal_Light.jpg)

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
