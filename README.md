# comp2017---assignment-2---solved
**TO GET THIS SOLUTION VISIT:** [COMP2017 –   Assignment 2 – Solved](https://mantutor.com/product/comp2017-assignment-2-solved/)


---

**For Custom/Order Solutions:** **Email:** mantutorcodes@gmail.com  

*We deliver quick, professional, and affordable assignment help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;88013&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;3&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (3 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COMP2017 - &nbsp; Assignment 2   - Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (3 votes)    </div>
    </div>
In this assignment you will be implementing and performing operations on a simple virtual machine. You will need to emulate this virtual machine to store and reference variables and stack frame contexts before reading a set of pseudo assembly instructions that dictate the operations that should be performed on the stack. Your program will take a single command line argument being the path to the file containing your x2017 assembly code.

Before attempting this assignment it would be a good idea to familiarise yourself with the stack, registers, stack frames, stack pointers, program counters, assembly and machine code. A strong understanding of these concepts is essential to completing this assignment. Section 3.6 and 3.7 of the course textbook provide specific detail to x86_64 architecture, however you can review these as a reference.

In order to complete this assignment at a technical level you should revise your understanding of bitwise operations, file IO, pointers and arrays.

Some implementation details are purposefully left ambiguous; you have the freedom to decide on the specifics yourself. Additionally this description does not define all possible behaviour that can be exhibited by the system; some error cases are not documented. You are expected to gracefully report and handle these errors yourself.

<h1>The Architecture</h1>
In this assignment you will be emulating an 8 bit architecture. The memory model of this architecture consists of:

<ul>
<li>RAM – Contains 2<sup>8 </sup>addresses of 1 byte each</li>
<li>Register Bank – 8 registers of 1 byte each</li>
<li>Program Code – Memory required to store the program to be executed.</li>
</ul>
For full marks the total size on disk of your program’s binary should not exceed 10kb.

1

During execution you should not store any information about the state of the machine outside of the RAM and the register bank.

Note: A register stores a single value using a fixed bit width. It the size of a register corresponding to the processor <em>word size</em>, in this case 8 bits. Think of them as a primitive variable. Physical processor hardware is constrained, and the number of registers is always fixed. There are registers which serve specific purposes, and those which are general. Please identify these in the description and consider them for your solution. You need not consider special purpose registers, such as floating point, in this assignment.

<h1>Program Code: x2017</h1>
Our virtual machine will be operating on a home brewed ‘x2017’ assembly language. You will be provided with binaries in this language to run on your virtual machine. Each operation within ‘x2017’ contains an operation specifier code (op code) and takes zero, one or two arguments. Arguments are expressed as one of four different types, while operation codes are selected from a table. The arguments of each function precede the opcode and are expressed as follows:

([Second Value][Second Type])([First Value][First Type])[Operation Code]

A collection of these operations will form a function.

The type is a two bit field and specifies the type of the preceding value.

<ul>
<li>– value: 1 byte long. The value in the preceding 8 bits should be interpreted as a single byte value.</li>
<li>– register address: 3 bits long. This address refers to one of the eight fixed registers</li>
<li>– stack symbol: 5 bits long. This refers to a particular symbol within the current stack frame.</li>
<li>– pointer valued: 5 bits long. This treats the contents of the address referred to by a particular symbol within the current stack frame as a variable. Pointers may reference variables on different stack frames.</li>
</ul>
The second address and address type field is optional and will not be required for unary operations. The address type specifies whether it is a stack address, a value, a register address or a pointer to another stack address. Stack addresses are 8 bits long, register addresses are 3 bits long and values are 8 bits long and pointer addresses are also 8 bits long.

A stack symbol is a value that is associated with an address on the stack; it is up to you to find a cogent method of allocating stack space to symbols. Symbols only exist within the scope of the current function; should two functions use the same symbol then they are not referencing the same region of memory.

While the exact memory layout within the stack frame is open to interpretation, four registers are reserved for special values.

<ul>
<li>0x07 Stores the program counter.</li>
<li>0x06 Will not be referenced by the program; this register exists for your personal use.</li>
<li>0x05 Will not be referenced by the program; this register exists for your personal use.</li>
<li>0x04 Will not be referenced by the program; this register exists for your personal use.</li>
</ul>
Registers in the range 0x00-0x03 are general purpose registers and may be explicitly referenced by a program.

The opcodes associated with ‘x2017’ instructions are detailed below. You will need to read each of the op-codes and implement the operation on the memory specified.

Opcodes:

000 – [MOV A B] – Copies the value at some point <em>B </em>in memory to another point <em>A </em>in memory

(register or stack). The destination may not be value typed.

001 – [CAL A] – Calls another function the first argument is a single byte (using the VALUE type) containing the label of the calling function.

010 – [RET] – Terminates the current function, this is guaranteed to always exist at the end of each function. There may be more than one RET in a function. If this function is the entry-point, then the program terminates.

011 – [REF A B] – Takes a stack symbol <em>B </em>and stores its corresponding stack address in <em>A</em>.

<ul>
<li>– [ADD A B] – Takes two register addresses and ADDs their values, storing the result in the first listed register.</li>
<li>– [PRINT A] – Takes any address type and prints the contents to a new line of standard output as an unsigned integer.</li>
<li>– [NOT A] – Takes a register address and performs a bitwise not operation on the value at that address. The result is stored in the same register</li>
<li>– [EQU A] – Takes a register address and tests if it equals zero. The value in the register will be set to 1 if it is 0, or 0 if it is not. The result is stored in the same register.</li>
</ul>
The state of the registers is preserved between CAL and RET operations.

In the event that the execution of this program enters an undefined state; for example if the amount of stack memory required to execute the program exceeds the RAM buffer, then you should print an appropriate error to standard error and return 1 on exiting main.

The value of the program counter register should reference the current opcode. Your program should increment the program counter before executing the associated instruction. You may wish to consider what may happen when the program counter is modified during the execution of an instruction.

Binary File Format:

The first few bits of the file are padding bits to ensure that the total number of bits in the file accumulates to a whole number of bytes. The number of padding bits will always be strictly less than one byte.

The file is broken up into a number of functions. Each function is defined with a three bit header dictating the ’label’ of the function, and a five bit tail specifying the number of instructions in the function. The function with the label 0 is the entry point and should be executed first.

[Padding bits]

[<strong>function </strong>label (3 bits)]

[OPCODE]

[OPCODE] …

[RET]

[Number of instructions (5 bits)] [<strong>function </strong>label (3 bits)]

[OPCODE]

[OPCODE] …

[RET]

[Number of instructions (5 bits)]

<h1>Example</h1>
The following assembly function moves the values 3 and 5 to separate registers before adding them, moving the value to the stack and returning.

Some equivalent C code might look like this:

<em>#define BYTE unsigned char </em><em>// Because all values are 1 byte </em><strong>void </strong>main()

{ <strong>register </strong>BYTE reg_0 = 3; <em>// Storing the value 3 at register 1 </em><strong>register </strong>BYTE reg_1 = 5; <em>// Storing the value 5 at register 2</em>

reg_0 += reg_1; <em>// ADD The two registers, save the value at r1 </em>BYTE A = reg_0; <em>// Store the value from register 1 at stack symbol A</em>

<strong>return</strong>; <em>// Return</em>

}

We can consider some equivalent x2017 assembly:

FUNC LABEL 0

MOV REG 0 VAL 3

MOV REG 1 VAL 5

ADD REG 0 REG 1

MOV STK A REG 0

RET

And this assembly can be compiled down to binary:

00000 <em># Padding for the file </em>000 <em># Function labeled 0</em>

00000011|00|000|01|000 <em># MOV REG 0 VAL 3</em>

00000101|00|001|01|000 <em># MOV REG 1 VAL 5</em>

001|01|000|01|100&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <em># ADD REG 0 REG 1</em>

000|01|00000|10|000&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <em># MOV STK A REG 0</em>

010&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <em># RET</em>

00101 <em># Number of instructions in the function</em>

Or without the comments:

0000000000000011000000100000000101000010

1000001010000110000001000001000001000101

And finally; hex formatted:

<strong>\x</strong>00<strong>\x</strong>03<strong>\x</strong>02<strong>\x</strong>01B<strong>\x</strong>82<strong>\x</strong>86<strong>\x</strong>04<strong>\x</strong>10E

Your program will take the path to one of these binary files as a command line argument and execute the instructions within.

<h1>Milestone</h1>
As part of this assignment, you are expected to submit a milestone prior to your final submission. The milestone task will be to create a disassembler for x2017 binaries. That is; your program will take an x2017 binary and print its contents in a human readable form. Given a path to a file containing:

<strong>\x</strong>00<strong>\x</strong>03<strong>\x</strong>02<strong>\x</strong>01<strong>\x</strong>42<strong>\x</strong>82<strong>\x</strong>86<strong>\x</strong>04<strong>\x</strong>10<strong>\x</strong>45 You would be expected to print:

FUNC LABEL 0

MOV REG 0 VAL 3

MOV REG 1 VAL 5

ADD REG 0 REG 1

MOV STK A REG 0

RET

You may notice that the symbol information is stripped in the binary; that is that the value ‘A’ never appears. You should print each unique symbol within each stack frame as a single capital letter in order of appearance starting with ‘A’. As there are 2<sup>5 </sup>possible symbols and only 26 letters of the alphabet symbols after <em>Z </em>should instead be displayed as lower case letters starting at <em>a</em>.

Indentation in the output of this program should be performed using four spaces.
