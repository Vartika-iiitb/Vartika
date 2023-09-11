
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

# Day 2: Introduction to ABI and Basic Verification Flow

<details>
  <summary>
    Application Binary Interface
  </summary>

An **Application Binary Interface (ABI)** is a set of conventions and specifications that dictate the low-level interface between software components, specifically between different binary programs or modules. The ABI defines how these components interact at the machine code level, ensuring that compiled code from different sources can work together seamlessly, regardless of how they were developed.

Key aspects of an ABI include:

1. Data Representation: How different data types are represented in memory and how they are passed between functions or modules. This includes details about byte ordering, data alignment, and structure layout.

2. Function Calling Convention: How functions are called and how parameters are passed between the caller and the callee. This includes information about register usage, stack management, and return values.


![Screenshot from 2023-08-23 01-51-24](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/35b72550-f3c9-4f37-82dc-8b783725d39e)

**Memory Allocation**

  ![Screenshot from 2023-08-23 01-53-50](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/582bf7ca-7f04-4573-bafa-b4842519c521)

</details>

<details>
  <summary>
    Lab Work Using ABI function calls
  </summary>

  Let us use the same example of sum of 'n' numbers in c-language but using a different approach.The algorithm used to re-write the code is shown here:

  ![Screenshot from 2023-08-23 02-37-34](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/ca178c13-05b5-4a00-aada-2a9b869de74d)

A C file with name 1to9_custom.c has the following code in it:

```
#include <stdio.h>

extern int load(int x, int y);

int main() {
	int result=0;
	int count = 0;
	result = load(0x0, count+1);.global load
	printf("Sum of number 1 to %d is %d\n", count,result);
}
```
Now Create another file named load.s and dump the following code into it:

```
.section .text
.global load
.type load, @function

load:
	add	a4,a0,zero
	add	a2,a0,a1
	add	a3,a0,zero
loop:
	add	a4,a3,a4
	addi	a3,a3,1
	blt	a3,a2,loop
	add	a0,a4,zero
	ret
```

</details>

<details>
  <summary>
    Basic verification flow using iverilog
  </summary>
  
  We are going to follow this Procedure in the later lab session:

![Screenshot from 2023-08-23 02-19-55](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/1775eaea-01a4-4ea9-84a8-c46f730273ae)

  
  **LAB : Run C program on RISC-V CPU**
  Commnad used for the RISC-V CPU Program code:
  
```
git clone https://github.com/kunalg123/riscv_workshop_collaterals.git
cd ~/riscv_workshop_collaterals/labs/
chmod 777 rv32im.sh
./rv32im.sh
```

  The output shown below:
  
  ![Screenshot from 2023-08-23 02-30-41](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/d9864375-13aa-414e-b57d-d93c68624c8a)

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

  ![Screenshot from 2023-08-22 22-08-23](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/8fd17574-6c64-4b79-9946-5fa3c3114406)


After building up strong basics built in TL-Verilog and digital design, and getting completely familiar with the Makerchip Platform, it was time to move on to the core aspect of the workshop, i.e. to build a RISC V core. On this day , the following basic blocks were implemented :

**1. Program Counter (PC)**

A program counter, also known as the instruction pointer, instruction address register, or sequence control register, is a register in a computer processor that contains the address of the next instruction to be executed from memory.As each instruction is fetched, the program counter increases its stored value by 1. After each instruction is fetched, the program counter points to the next instruction in the sequence. The address specified by the PC will be + n (+1 for a 1-word instruction and +2 for a 2-word instruction) each time one instruction is executed. In the case of an interrupt instruction, the jump destination address is stored.0 The program counter is a fundamental component of a computer's central processing unit (CPU).

**2. Imem-Rd ( Instruction Memory)**

The "instruction memory" refers to a component or subsystem that stores and provides instructions to the processor. It is an essential part of the overall processor architecture, especially in the context of the RISC-V instruction set architecture (ISA).
he instruction memory's main function is to hold the machine code instructions that the processor fetches, decodes, and executes to perform various tasks and operations.

**3. Instruction Decoder**

The "instruction decoder" is a crucial component responsible for interpreting the fetched machine code instructions and determining the appropriate actions that the processor needs to take in order to execute the instruction. It plays a central role in the instruction execution process and is typically located after the instruction fetch stage and before the execution units in the processor pipeline.

**4. Register File**

The register file is a storage component that holds the processor's general-purpose registers. These registers are used for temporary storage of data during instruction execution. In RISC-V, the register file contains a fixed number of registers (e.g., 32 registers in a standard RISC-V implementation).

**5. Arithmatic Logic Unit (ALU)**

In the RISC-V architecture, the ALU (Arithmetic Logic Unit) is responsible for performing arithmetic and logical operations on binary data. It is a critical component within the processor that executes instructions by manipulating data according to the instruction's operation code (opcode) and operands.


Thus the instruction set architecture of base integer instructions, next_pc logic, the register file, ALU, branch instructions, etc. and eventually the CPU core was built and tested, using appropriate testbench logic, and assembly code developed on Day 2, by the end of the day.
</details>

<details>
  <summary>
    Fetch and Decode
  </summary>
  The Implementation plan of risc-V code:
  
![Screenshot from 2023-08-22 23-38-54](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/14eb2bd1-4f92-4aab-aa91-68f03d466a66)

**Lab - PC**

The Implementation pipeline:

![Screenshot from 2023-08-22 23-39-08](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/dde8aa89-8aea-49ed-a7a4-f3381da83508)

**The Makerchip output**

![Screenshot from 2023-08-22 23-43-23](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/90438411-a6a2-47c6-834f-319fab418a71)



<strong>Lab - Fetch</strong>



**The pipeline structure( part 1)**

![Screenshot from 2023-08-22 23-46-32](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/369fe660-e114-4cea-8d4f-6912044a0855)


**The pipeline structure( part 2)**  

![Screenshot from 2023-08-22 23-46-58](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/791a9d4b-1a3a-4748-95b4-75c02b6eb405)

**The Makerchip output**

![Screenshot from 2023-08-22 23-49-05](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/b80b30f3-fc32-4c6e-954f-0d820f192180)

   
**Lab - Instruction Type Decode**

**The Pipeline Structure**

![Screenshot from 2023-08-23 00-33-44](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/9d5169e3-8d4e-48ad-9ce6-9ee561a7f565)

**The Makerchip output**

![Screenshot from 2023-08-23 00-34-04](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/b0bf171f-7dfb-4e9f-bd34-6ecd6890daca)


**Lab - Instruction Immediate Decode**


![Screenshot from 2023-08-23 00-36-20](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/74f5ff07-ca65-4519-85ea-c88143a25f1b)

**The Implementation Output**

![Screenshot from 2023-08-23 00-35-39](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/b3828b31-a98f-43b8-8802-12f2800290dd)


**Lab - Instruction Decode**

![Screenshot from 2023-08-23 00-39-43](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/702888c2-d8f2-48fe-a68f-7804b3ceabed)


**The Implementation Output**

![Screenshot from 2023-08-23 00-38-15](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/b8a58cd3-a8b0-46b5-b446-23270209306a)


**Lab - Instruction Field Decode**

![Screenshot from 2023-08-23 00-41-17](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/9d32a560-8448-489d-98e1-6784c77f0126)


Decoder 1:

![Screenshot from 2023-08-23 00-41-37](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/e7cfe728-8d0f-419d-a557-855f2832d0a2)


Decoder 2:

![Screenshot from 2023-08-23 00-42-12](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/50b09191-54e9-436d-8469-efe2a201a0b4)

</details>


<details>
  <summary>
    RISC-V control Logic
  </summary>

**Lab 1: Register File Read**

**Lab - Register file read - 1**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 00-48-53](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/bcb497e7-add6-4c34-b0ab-b8bf1e13f4bc)

The makerchip Output:

![Screenshot from 2023-08-23 00-52-02](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/c5f19837-4cff-4888-98a6-bb1973948cc7)


**Lab - Register file read - 2**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 00-49-15](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/4bfdab74-122d-47bb-8d79-7e82b6de9275)

The makerchip Output:

![Screenshot from 2023-08-23 00-52-02](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/4dcdc632-1940-40b9-abb2-cbc3dffc8350)

**Lab 2: ALU**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 00-54-13](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/0aad239e-4fe2-4899-b823-097f35f5bafb)

The makerchip Output:

![Screenshot from 2023-08-23 00-55-23](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/4ae9b14b-7b7b-47a8-89d2-aee57eabc8f0)


**Lab 3: Register File Write**

The Pipeline structure is as follows:


![Screenshot from 2023-08-23 00-57-47](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/72d3f8c5-3c76-467b-92a4-cdb1d492e4b3)



The makerchip Implementation Output:

![Screenshot from 2023-08-23 00-56-53](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/042da73f-594d-4008-bfb8-a000648e6abd)

**Lab 4: Branch Instruction**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 01-00-56](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/670bf006-a740-4ce7-a4c1-29ce59b3974e)


The makerchip Implementation Output:


![Screenshot from 2023-08-23 00-59-05](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/0d6baf8c-1f04-4f1b-bef1-0d90aed91a31)

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 01-01-30](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/ce2fbea6-1019-422c-8709-3bd0dda3591e)


The makerchip Implementation Output:

![Screenshot from 2023-08-23 01-01-46](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/e5ac00ec-c525-4ee7-8a5f-bcfefb3e1d37)


**Lab 5: Testbench**


The makerchip Implementation Output:

![Screenshot from 2023-08-23 01-03-04](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/3e6e5432-ac53-422c-aaac-93253ca3809b)


</details>

# Day 5 : Complete pipeline RISC-V CPU micro architecture

<details>
  <summary>
    Pipelining the CPU
  </summary>

  ![Screenshot from 2023-08-23 01-04-26](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/462d073a-053f-46e3-aa69-9f8f5666330b)


**Control flow Hazards**

Control flow hazards are situations in computer architectures where the normal sequential execution of instructions is disrupted due to the occurrence of branching or jumping instructions. These hazards can lead to incorrect program behavior, inefficiencies, and pipeline stalls. In the context of the RISC-V architecture, which uses pipelining to enhance performance, control flow hazards can have a significant impact on the efficiency of instruction execution. 

**Read after Write Hazards**

Read-after-write hazards, often abbreviated as RAW hazards, are a type of data hazard that can occur in computer architectures like RISC-V. These hazards arise when an instruction depends on the result of a previous instruction that writes to a register or memory location. In other words, an instruction attempts to read data before the previous instruction that writes to that data has completed its execution. This can lead to incorrect program behavior, as the dependent instruction might operate on stale or incorrect data.

In the context of the RISC-V architecture, which employs pipelining for improved performance, RAW hazards are particularly important to manage, as they can lead to pipeline stalls and reduced throughout. 

**Lab 1. Cycle valid signal**

The makerchip Implementation Output:

![Screenshot from 2023-08-23 01-09-19](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/866a44d0-88b1-4c5f-a294-770932471b09)


**Lab 2. Cycle RISC-V**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 01-10-50](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/1a4ec402-9a38-4b1d-863d-4d865eb97349)

The makerchip Implementation Output:

![Screenshot from 2023-08-23 01-11-01](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/fe883638-8ad3-4876-9064-a547f1f4b6e9)

</details>

<details>
  <summary>
    Solutions to Pipeline Hazards
  </summary>

**LAB - Register File Bypass**

The pipeline structure is shown below:

![Screenshot from 2023-08-23 01-37-55](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/66d0b7b4-4089-4bac-a3f0-c63656708de8)

The makerchip Implementation is shown below:

![Screenshot from 2023-08-23 01-40-39](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/55ec7e15-dc51-47dc-ad8d-06f76aefd9c0)

 **LAB - ALU**

The makerchip Implementation is shown below:

 ![Screenshot from 2023-08-23 01-42-41](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/70874d93-bb4f-417b-b3e8-c5030611ccad)

</details>

<details>
  <summary>
    Load/ Store Instructions and completing RISC-V CPU
  </summary>
  
**Load Instruction**

The pipeline structure is shown below:

![Screenshot from 2023-08-23 01-34-08](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/88862b44-4964-4664-acac-98ef9a64b314)


The Makerchip Implementation is as follows:

![Screenshot from 2023-08-23 01-32-20](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/9e06df4b-6c33-4f4a-b5f4-2b6b9cc82295)


**Load_store**

The pipeline structure is shown below:

![Screenshot from 2023-08-23 01-36-08](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/73833c44-706e-4494-8b2e-e26f431ae163)


The Makerchip Implementation is as follows:

![Screenshot from 2023-08-23 01-31-41](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/ce69232b-8be4-416d-9a8b-e409f2a85378)


**Jumps**

The Pipeline structure is as follows:

![Screenshot from 2023-08-23 01-29-21](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/969c0cee-24f6-457e-bf51-759a7b1bef74)


The makerchip Implementation Output:

![Screenshot from 2023-08-23 01-29-30](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/906150d1-f97a-4929-bf1c-e1523d3ca2ec)

  **Risc-V core CPU - Final Implementation:**

  ```
\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/vartika/RISC-V_MYTH_Workshop/c1719d5b338896577b79ee76c2f443ca2a76e14f/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   //
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   m4_asm(SW, r0, r10, 10000)           // Store the final result value to byte address 16
   m4_asm(LW, r15, r0, 10000)           // Load the final result value from adress 16 to x17
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)


   |cpu
      @0
         $reset = *reset;
         
         //MODIFIED NEXT PC LOGIC FOR INCLUDING BRANCH INSTRCUTIONS
         $pc[31:0] = >>1$reset ? 32'b0 :
                     >>3$valid_taken_branch ? >>3$br_target_pc :
                     >>3$valid_load ? >>3$inc_pc :
                     >>3$valid_jump && >>3$is_jal ? >>3$br_target_pc :
                     >>3$valid_jump && >>3$is_jalr ? >>3$jalr_target_pc :
                     >>1$inc_pc ;
         //START LOGIC TO PROVIDE FIRST VALID LOGIC
         //$start = (>>1$reset && $reset == 0) ? 1'b1 : 1'b0;
         //$valid = $reset ? 1'b0 :
                  //$start ? 1'b1 : >>3$valid;
     
      @1  
         //INSTRUCTION FETCH
         $inc_pc[31:0] = $pc + 32'd4;
         
         $imem_rd_en = !$reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         
         $instr[31:0] = $imem_rd_data[31:0];
         
         //INSTRUCTION TYPES DECODE        
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         $is_r_instr = $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b10100;
         
         $is_j_instr = $instr[6:2] ==? 5'b11011;
         
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11001;
         
         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         //INSTRUCTION IMMEDIATE DECODE
         $imm[31:0] = $is_i_instr ? {{21{$instr[31]}}, $instr[30:20]} :
                      $is_s_instr ? {{21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? {{20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? {{12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                                                            32'b0;
         //INSTRUCTION DECODE
         $opcode[6:0] = $instr[6:0];
         
         
         //INSTRUCTION FIELD DECODE
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
           
         $rs1_valid = $is_r_instr  || $is_s_instr || $is_b_instr || $is_i_instr;
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         
         $funct3_valid = $is_r_instr  || $is_s_instr || $is_b_instr || $is_i_instr;
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
           
         $funct7_valid = $is_r_instr ;
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
           
         $rd_valid = $is_r_instr  || $is_u_instr || $is_j_instr || $is_i_instr;
         ?$rd_valid
            $rd[4:0] = $instr[11:7];
         
         
      @2
         //INSTRUCTION DECODE
         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add = $dec_bits ==? 11'b0_000_0110011;
         $is_lui = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr = $dec_bits ==? 11'bx_000_1100111;
         $is_load = $opcode == 7'b0000011;
         $is_sb = $dec_bits ==? 11'bx_000_0100011;
         $is_sh = $dec_bits ==? 11'bx_001_0100011;
         $is_sw = $dec_bits ==? 11'bx_010_0100011;
         $is_slti = $dec_bits ==? 11'bx_010_0010011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0100011;
         $is_xori = $dec_bits ==? 11'bx_100_0100011;
         $is_ori = $dec_bits ==? 11'bx_110_0100011;
         $is_andi = $dec_bits ==? 11'bx_111_0100011;
         $is_slli = $dec_bits ==? 11'b0_001_0100011;
         $is_srli = $dec_bits ==? 11'b0_101_0100011;
         $is_srai = $dec_bits ==? 11'b1_101_0100011;
         $is_sub = $dec_bits ==? 11'b1_000_0110011;
         $is_sll = $dec_bits ==? 11'b0_001_0110011;
         $is_slt = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu = $dec_bits ==? 11'b0_011_0110011;
         $is_xor = $dec_bits ==? 11'b0_100_0110011;
         $is_srl = $dec_bits ==? 11'b0_101_0110011;
         $is_sra = $dec_bits ==? 11'b1_101_0110011;
         $is_or = $dec_bits ==? 11'b0_110_0110011;
         $is_and = $dec_bits ==? 11'b0_111_0110011;
         
         $jalr_target_pc[31:0] = $src1_value +$imm ;
      @3
         $is_jump = $is_jal || $is_jalr ;   
         `BOGUS_USE($is_beq $is_bne $is_blt $is_bge $is_bltu $is_bgeu $is_addi $is_add
                    $is_lui $is_auipc $is_jal $is_jalr $is_load $is_sb $is_sh $is_sw $is_slti
                    $is_sltiu $is_xori $is_ori $is_andi $is_slli $is_srli $is_srai $is_sub $is_sll
                    $is_slt $is_sltu $is_xor $is_srl $is_sra $is_or $is_and)
         
      @2  
         //REGISTER FILE READ
         //$rf_wr_en = 1'b0;
         //$rf_wr_index[4:0] = 5'b0;
         //$rf_wr_data[31:0] = 32'b0;
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         $src1_value[31:0] = >>1$rf_wr_en && (>>1$rf_wr_index == $rf_rd_index1) ? >>1$result : $rf_rd_data1;
         $src2_value[31:0] = >>1$rf_wr_en && (>>1$rf_wr_index == $rf_rd_index2) ? >>1$result : $rf_rd_data2;
         $br_target_pc[31:0] = $pc +$imm;
         
      @3  
         //ARITHMETIC AND LOGIC UNIT (ALU)
         
         $sltu_rslt[31:0] = $src1_value < $src2_value;
         $sltiu_rslt[31:0] = $src1_value < $imm;
         $result[31:0] = $is_addi ? $src1_value + $imm :
                         $is_add ? $src1_value + $src2_value :
                         $is_andi ? $src1_value & $imm :
                         $is_ori ? $src1_value | $imm :
                         $is_xori ? $src1_value ^ $imm :
                         $is_slli ? $src1_value << $imm[5:0] :
                         ($is_addi || $is_load || $is_s_instr) ? $src1_value + $imm :
                         $is_srli ? $src1_value >> $imm[5:0] :
                         $is_and ? $src1_value & $src2_value :
                         $is_or ? $src1_value | $src2_value :
                         $is_xor ? $src1_value ^ $src2_value :
                         $is_sub ? $src1_value - $src2_value :
                         $is_sll ? $src1_value << $src2_value[4:0] :
                         $is_srl ? $src1_value >> $src2_value[4:0] :
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ? {$imm[31:12],12'b0} :
                         $is_auipc ? $pc + $imm :
                         $is_jal ? $pc + 4 :
                         $is_jalr ? $pc + 4 :
                         $is_srai ? { {32{$src1_value[31]}},$src1_value} >> $imm[4:0] :
                         $is_slt ? ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0,$src1_value[31]} :
                         $is_slti ? ($src1_value[31] == $imm[31]) ? $sltiu_rslt : {31'b0,$src1_value[31]} :
                         $is_sra ? { {32{$src1_value[31]}},$src1_value} >> $src2_value[4:0] :
                         32'bx;
         
         
         //REGISTER FILE WRITE
         $rf_wr_en = ($rd_valid && $rd != 5'b0 && $valid) || >>2$valid_load;
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd;
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data : $result;
         
         
         //BRANCH INSTRUCTIONS 1
         $taken_branch = $is_beq ? ($src1_value == $src2_value):
                         $is_bne ? ($src1_value != $src2_value):
                         $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])):
                         $is_bltu ? ($src1_value < $src2_value):
                         $is_bgeu ? ($src1_value >= $src2_value):
                         1'b0;
          //CYCLE VALID INSTRUCTIONS
         $valid = !(>>1$valid_taken_branch || >>2$valid_taken_branch ||
                    >>1$valid_load || >>2$valid_load) ;
         
         $valid_load = $valid && $is_load ;
         //$valid = !(>>1$valid_taken_branch || >>2$valid_taken_branch);
         $valid_taken_branch = $valid && $taken_branch;
         $valid_jump = $is_jump && $valid ;
         `BOGUS_USE($taken_branch)
      @4
         //MINI 1-R/W MEMORY
         $dmem_wr_en = $is_s_instr && $valid ;
         $dmem_addr[3:0] = $result[5:2] ;
         $dmem_wr_data[31:0] = $src2_value ;
         $dmem_rd_en = $is_load ;
         
      @5
         //LOAD DATA
         $ld_data[31:0] = $dmem_rd_data ;   
         
         
         

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   //*passed = *cyc_cnt > 40;
   *passed = |cpu/xreg[15]>>5$value == (1+2+3+4+5+6+7+8+9) ;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)
   
   m4+viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic
   //@4 would work for all lab
\SV
   endmodule
```
The Makerchip Implementation Output:

![Screenshot from 2023-08-23 01-27-51](https://github.com/Vartika-iiitb/Vartika_RISC-V/assets/140998716/6447df87-ed96-4629-bf9b-4566bf341737)

</details>

# References

<summary>

  https://en.wikipedia.org/wiki/RISC-V

  https://github.com/stevehoover/RISC-V_MYTH_Workshop

  https://makerchip.com/sandbox/0ERfWhNWz/0r0hpq

  https://makerchip.com/sandbox/#
  
</summary>
