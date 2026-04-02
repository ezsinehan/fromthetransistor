### Sinehan's Dev Notes! (4section1)

#### Section 1: Intro: Cheating our way past the transistor -- 0.5 weeks
- So about those transistors -- Course overview. Describe how FPGAs are buildable using transistors, and that ICs are just collections of transistors in a nice reliable package. Understand the LUTs and stuff. Talk briefly about the theory of transistors, but all projects must build on each other so we can’t build one.
- Emulation -- Building on real hardware limits the reach of this course. Using something like Verilator will allow anyone with a computer to play.

- Okay lets pull exactly the problems I need to solve to reach understanding nothing more nothing less...
  - What are FPGAs?
    - Watching -- https://www.youtube.com/watch?v=lLg1AgA2Xoo -- Introduction to FPGA Part 1 - What is an FPGA? | Digi-Key Electronics
      - FPGA stands for Field Programmable Gate Array
      - An integrated circuit or chip that allows you to design completely custom digital logic
      - Allows for creation of custom digital circuits
      - Made up of a bunch of logic cells that act as fundamental building blocks for creating digital circuits
        - You can configure the individual cells to operate in certain ways and connect the cells together to form any number of digital circuits
        - We also have access to clock signals and block of ram for storing data -> they can have other peripherals like analog to digital converts or analog outputs
        - Cells are often grouped into logic blocks and this reconfigurable group of interconnected hardware is referred to as the FPGA fabric
          - eg you can use these building blocks to make your own processor in the FPGA and it allows you to run code like you would on a micro controller or micro processor(maybe more than one processor if you have the space)
          - creation of softcore processor is popular since you can connect it to different digital circuits you create on the FPGA fabric
      - Why use an FPGA?
        - Custom, reconfigurable digital logic circuits
        - Add peripherals
        - Modify CPU
        - Speed for specific computations
      - Design Flow:
        - 1. First write code in HDL(Verilog)
        - 2. Then simulate design(using gtkwave as visualize)
        - 3. Next we synthesize our code(yosys) -> take the HDL code and translate it into gate level representations(output looks like netlist) this tells the FPGA how the various cells, logic and, registers should be connected
        - 4. However the netlist will be generic and our specific FPGA would not know what todo with it and so we have Place and Route step which will convert the netlist output by the synthesis step to the actual gate and wire connections that need to be made in our particular FPGA(nextpnr) -> the output is an ascii file which tells the FPGA exactly what it needs to do in order to create the circuit in our code
        - 5. Next convert this mainly human readable ascii format so the package step(icepack) to convert it to binary file that can be actually read by the FPGA configuration process 
        - 6. Finally upload(iceprog) to upload that binary to the external flash memory chip connected to the FPGA
        - So we don't have to remember these tool names or call each step we can use APIO which will call these low level tools for use
        - Note that these colleciton of tools only work with the Lattice ice40 line of FGPA
  - Okay I think I kinda understand what FPGAs are now.... but do I build them with a transistor?
    - What the fuck is a transistor?
      
