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
<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/VGAPrjSum.png">

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
## **My VGA Design Edit**
My plan was to combine both VGAStripes and VGAColourCycle and create several static images of varying complexity and cycle between them. I believed that this would be achievable for me; if I could not get ColourCycle to work, I would just try to create the most complicated image I could. As a result, I decided to start with the flag of Norway. 
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.

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
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.


Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/martaprietos/SoC-Verilog-Project/main/docs/assets/images/VGAPrjSrcs.png">
