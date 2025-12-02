---
layout: home
title: FPGA VGA Driver Project
tags: Marta Prieto
categories: demo
---

This page is dedicated to tracking the prpgress of my SOC FPGA Project. the aim of this project is to use what I learn in my System on Chip Design module to create an FPGA project that will display a custom set of images on a 640x480 display.
### **Project Set-Up**

I started by using a USB cable to connect the board to my computer to allow me to upload my image code, then I used a VGA cable to connect my board via the VGA port to my second monitor.I worked on a local folder on my machine as there were permission restrictions on OneDrive. I created a file called ATU on the C drive and then another file inside called VS where I put all my project files.
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/filesystem.png">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/stripesSummary.png">

I began coding by using a template Vivado project we were given and adapting it to practise creating different images.
The first step in creating a custom image was reverse-engineering the template code to figure out how each pixel was being coloured. I used a pen and paper to calculate the width of each stripe and practised changing their colour. Then I changed the code to create horizontal rows of colour, rather than vertical lines.
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/firstImage.jpeg">
### **Simulation**
Simulation is the first major step in Vivado's compilation process. Using the simulation buttom, I was able to verify that all my signals were behaving as expected and could move on to synthesis. There were a few instances where I tried to run synthesis but had forgotten to move my Testbench file to the top of my Simulation Sources section. Once the files were properly arranged, it ran as normal, though it often took a long time to compile
### **Synthesis and Implementation**
The next step in the compliling process is synthesis. Synthesis converts the code into gates and translates their behaviour. Vivado then runs implementation which places and routes these logic gates. Implementation assigns logic to the FPGA board and checks timing constraints. Once all this work is done, it will generate the bitstream.
### **Demonstration**
Once the bitstream was generated, I opened the hardware manager and programmed the board. After I switched to VGA on my monitor, I was able to see the design. In this case, I was viewing the template code file titled ColourStripes
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/colourStripes.png">
### **My VGA Design Edit**
My plan was to combine both VGAStripes and VGAColourCycle and create several static images of varying complexity and cycle between them. I believed that this would be achievable for me; if I could not get ColourCycle to work, I would just try to create the most complicated image I could. As a result, I decided to start with the flag of Norway. 
### **Code Adaptation**
In VGAStripes I first created a fully red background, the practised adding two lines to make a cross on top.
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/netherlandsFirst.jpeg">

Once I positioned the cross in a way I liked, I tried to add the blue cross on top. I initially tried to include it in my white cross if statement, but realised that if I did, once the column was drawn, the white row would cut off a portion of the blue, leaving a gap. I separated them out into two if statements and this resolved the issue as all of the white would be coloured before the blue gets added on top.
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/whiteRedNetherlands.png">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/whiteBlueNetherlands.png">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/netherlands.jpeg">

From here I created several more flags icluding Ireland, France, Sweden, and Belgium, following largely the same process of trial and error. 
I used <a href="https://oatcookies.neocities.org/twelvebitcolor"> this website </a> to find the 12-bit RGB value of each colour I used.
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/ireland.jpeg">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/france.jpeg">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/sweden.jpeg">
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/belgium.jpeg">
### **Simulation, Synthesis, and Implementation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
When I first created the project, I ran each step separately to better understand the errors I was getting. 
To avoid any errors, instead of doing each compiling step one by one, I used the "Generate Bitstream" button which does all 3 steps automatically.

### **Errors**
One of the longest running and most frustrating errors I ran into was when, no matter what I tried, I could not get the board to display any flag other than the Irish one. A nice display of patriotism, my hypothesis was that the board seemed to think that every state depicted the Irish colours, and that the code actually was cycling through them. I tried reducing the states to just two, Ireland and France, then removed Ireland entirely and replaced it with Sweden. Still, I couldn't get it to change. I compared my code with the template code and I used the AI tools available to us to try. Eventually, after nearly a full lab session of troubleshooting, I finally realised that when I clicked "Generate Bitstream", Vivado was using an old design from another file rather than creating one from the current project. 

I remembered that at the start of the lab, after I had opened the correct file, I had been asked by a classmate to open that old file so they could compare our layouts. When they were finished, I shut down the old one and continued to work. Despite closing down the old project, because it was my most recently opened project, Vivado decided to use that to generate the bitstream.

### **Demonstration**
Once I figured this out I was able to reprogram my board correctly. I was finally able to get each flag showing one by one. I had hoped to add a few more flags, but ran out of time. If I had a few more weeks I would try to create a some more complicated images. 
I knew I prefered having a small number of simple images that can be cycled through, than only one or two complicated images that I cannot cycle between. By doing the former, I was able to demonstrate an understanding of both ColourStripes and ColourCycle.
<br>
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/finalProjVideo.gif">
