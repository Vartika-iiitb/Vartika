
# Vartika_RISC-V


# Day 1: Introduction to Risc-V ISA and GNU Compiler Toolchain

<details>
  
  <Summary>
    Introduction to RISC-V basic Keywords
  </Summary>


  RISC-V is an open standard instruction set architecture (ISA) based on reduced instruction set computer (RISC) principles. Unlike most other ISA designs, it is provided under royalty-free open-source licenses.RISC-V is a completely open architecture, allowing anyone to create processors based on the design or create improvements without complicated licensing agreements. RISC-V is a popular alternative to proprietary architectures available today, such as those by ARM. The concept behind RISC-V was motivated by the truth that most of the processor instructions were not utilized by most computer programs, so unnecessary decoding logic was being utilized within the designs of processors, consuming more power and area. The RISC-V processor was implemented to shorten the instruction set and invest more within register resources.
</details>

<details>
  <summary>
     From Apps to Hardware
  </summary>

  The Applications that we generally use enters into the system software and then system software converts High Level Language into Assembly language and subsequently into binary form.
  
 System software has three components:
 1. Operating system
 2. Compiler
 3. Assembler

System software performs the following tasks:
1. It handles the I/O operations
2. It allocates the memory
3. It is low level system function
4. It takes the high level language and converts into binary.

  Following figure correctly depicts the flow diagram of system software.
  
![ProgLanguages06](https://github.com/Vartika-iiitb/Vartika/assets/140998716/3a49823c-7928-4749-89f5-23c291410813)

</details>

<details>
  <summary>
    Detailed Description of Course Content
  </summary>
 
In this section, we are going to see the we will see the basic operations of C program.

**Illustration 1: Integer Addition and Integer Multiplication using C program**

![Screenshot from 2023-08-18 18-00-07](https://github.com/Vartika-iiitb/Vartika/assets/140998716/180e98cd-610f-409f-94c0-f26b6e1fd7d5)


![Screenshot from 2023-08-18 16-30-58](https://github.com/Vartika-iiitb/Vartika/assets/140998716/f2d1b9d5-a164-4af4-b9f3-6c07fbe9d555)


![Screenshot from 2023-08-18 16-31-30](https://github.com/Vartika-iiitb/Vartika/assets/140998716/b9dfd545-d270-4a2c-93e7-4dd8c5992197)


![Screenshot from 2023-08-18 16-33-01](https://github.com/Vartika-iiitb/Vartika/assets/140998716/ee3ca8fe-35d9-408c-be6a-1a893afbcd64)


![Screenshot from 2023-08-18 16-34-35](https://github.com/Vartika-iiitb/Vartika/assets/140998716/0c00e125-bbe6-49aa-8245-a639c4ae9397)


**Illustration 2: Floating numbers addition and multiplication using C programming:**

![Screenshot from 2023-08-18 16-34-49](https://github.com/Vartika-iiitb/Vartika/assets/140998716/6414b8b7-3def-4358-8109-dc40a3345994)

The Screenshot given below depicts the registers which provides the system codes which are available for the programmers to use and understand.

![Screenshot from 2023-08-18 16-52-51](https://github.com/Vartika-iiitb/Vartika/assets/140998716/bd880f84-1680-4072-9efa-90ef59d7e00d)


The Screenshot given below depicts the Memory Allocation and stack pointer. it is used for transfering datas from Registers to the memory, or any data transfer happening between memory, stack pointer and the registers:

![Screenshot from 2023-08-18 16-55-12](https://github.com/Vartika-iiitb/Vartika/assets/140998716/b7bc97d7-eb40-4fc9-9208-5348ddb41582)

</details>

<details>
  <summary> 
C program to compute number from 1 to n
 </summary>

The following Screenshot shows the C code to calculate the sum of numbers from 1 to n:

![Screenshot from 2023-08-19 17-28-13](https://github.com/Vartika-iiitb/Vartika/assets/140998716/94844bdd-fe57-4f80-a329-50ae30760f90)

The command used:

```
gcc sum1ton.c
./a.out

```

![Screenshot from 2023-08-19 17-27-52](https://github.com/Vartika-iiitb/Vartika/assets/140998716/77892bc3-a6ef-4a17-8231-3748f2b89d10)

</details>


# Day3 : Digital logic with TL- verilog and makerchip

<details>
  <summary>  
 Combinational logic with TL-verilog using makerchip
  </summary>
  
   **Introduction to Logic Gates**

  The Screenshot below depicts different logic gates with their corresponding Truth Table:
  However if we have nand gate then one can make different logic gates with Nand gate.
  
![Screenshot from 2023-08-20 19-29-42](https://github.com/Vartika-iiitb/Vartika/assets/140998716/eb29e0bc-8874-480a-9e6f-7bc24f1935a2)

The Screenshort shown below depicts the Boolean operator

![Screenshot from 2023-08-20 19-40-52](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/e4219257-1424-49bf-9259-d79dd92f2e41)

**Illustration 1: Combinational Logic - Basic MUX Implementation using Makerchip**

![Screenshot from 2023-08-20 19-43-19](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/3c1c55cd-a375-4e9d-b256-dc89599b9411)

![Screenshot from 2023-08-20 19-45-49](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/a6882b64-74f0-4c4f-911a-f742955b1a09)


![Screenshot from 2023-08-20 20-07-30](https://github.com/Vartika-iiitb/Vartika/assets/140998716/7d09c56a-9f1a-4807-b8ed-7025f5c859a9)

**Illustration 2 : Combinational Calculator using Makerchip**

  ![Screenshot from 2023-08-20 23-06-13](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/e11259d5-3f2a-43fb-a6c7-4a2b0a8e5ce3)

**Illustration 3 : FPGA Multiplier using Makerchip**

![Screenshot from 2023-08-20 23-27-39](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/7fe22fc2-6747-43e3-a566-5af380f2368b)

**Illustration 4 : Ripple Carry adder using Makerchip**

![Screenshot from 2023-08-20 19-36-36](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/8e30a13d-80d3-4942-837c-ea72ec9a0c4e)


![Screenshot from 2023-08-20 23-31-55](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/4bd8a40a-fd40-4e01-a64f-e4be59a09a32)

</details>

<details>
<summary>  
 Sequential logic with TL-verilog using makerchip
</summary>

**What is TL verilog?**

TL-Verilog is a Verilog implementation of TL-X, a language extension that extends any HDL with transaction-level modeling. It is specifically designed for modeling hardware and provides abstract context suited to hardware design with numerous benefits. TL-Verilog eliminates the need for legacy language features of Verilog and introduces simpler syntax. It adds powerful constructs for pipelines and transactions, making it more powerful and has a significant code reduction as compared to other HDL languages.TL-Verilog is built for the design process, not for the mere description of static designs. TL-VHDL is a project that aims to layer transaction-level support on other languages to broaden the reach of the technology.

**Illustration 5 : Fibonacci series**

![Screenshot from 2023-08-20 23-44-16](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/e944c5ef-e779-42de-8479-2d238999ff73)

**Illustration 6 : Simple Pythagoras Example**

![Screenshot from 2023-08-20 23-48-47](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/4ea4be44-be88-4978-86b4-9a446719d5a3)

![Screenshot from 2023-08-20 23-50-22](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/a92db598-e5b6-41f6-8195-a676ea074392)


</details>

<details>
  <summary>
    Pipelining
  </summary>

  Pipelining is a design technique used to improve the throughput of a digital system by breaking down the processing of a task into multiple stages, with each stage performing a specific operation on the data. In traditional Verilog, describing pipelined designs can be quite verbose and require manual management of pipeline registers. TL Verilog simplifies this process by introducing constructs that allow you to define pipelines more easily.

In TL Verilog, the pipelining feature allows you to specify the pipeline stages, their functionality, and the data flow between them using high-level constructs. This abstraction can help designers focus on the functional aspects of the pipeline rather than getting bogged down in the low-level implementation details.

**Illustration 7 : Implementation of pipelining through TL verilog**

![Screenshot from 2023-08-20 23-54-46](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/773121dc-33c6-443f-9988-e33b86f8ba75)

**Illustration 8 : Distance Accumulator**

The screenshot shown below depicts the pipelining of the Distance Accumulator:

![Screenshot from 2023-08-21 00-02-31](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/84eab665-0dde-4dbb-b3bf-d095840a552f)

![Screenshot from 2023-08-21 00-02-52](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/0180b973-2e21-4feb-92de-3ac60abddccc)



**Illustration 9 : 2-cycle Calculator**

![Screenshot from 2023-08-21 00-21-52](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/3eb4ad4b-2d7c-4362-af73-c7606fbc8664)

</details>

<details>
  <summary>
    Wrap up
  </summary>

  **Illustration 10 - Conway game of life**

  Here in each cycle, the liveness of a cell (square in the grid) is based on its eight neighboring cells (horizontally, vertically, and diagonally). An empty cell comes to life if it had exactly three live neighbors. It dies if it has fewer than two live neighbors (starvation) or more than three (overpopulation).

This example implements Conway’s Life. The grid is constructed using behavioral hierarchy.

![Screenshot from 2023-08-21 00-49-18](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/3cf06db0-3d62-4777-9c2a-b127f28a07fd)

</details>

# Day 4 : Basic RISC-V micro architecture

<details>
  <summary>
    Introduction to simple RISC-V micro architecture
  </summary>
</details>

<details>
  <summary>
    Fetch and Decode
  </summary>
</details>

<details>
  <summary>
    RISC-V control Logic
  </summary>
</details>

# Day 5 : Complete pipeline RISC-V CPU micro architecture

<details>
  <summary>
    Pipelining the CPU
  </summary>
</details>

<details>
  <summary>
    Solutions to Pipeline Hazards
  </summary>
</details>

<details>
  <summary>
    Load/ Store Instructions and completing RISC-V CPU
  </summary>
</details>

# References

<summary>

  https://en.wikipedia.org/wiki/RISC-V

  https://github.com/stevehoover/RISC-V_MYTH_Workshop

  https://makerchip.com/sandbox/0ERfWhNWz/0r0hpq

  https://makerchip.com/sandbox/#
  
</summary>
