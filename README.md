java c
Lab 7: Four-Function Calculator
Sequential Design III
Total Points: 150
Overview
We are all familiar with the basic four-function calculator which has evolved over the years from the ancient two-function (addition and subtraction) abacus to today's ubiquitous app on our mobile devices (check out this history of the calculator (https://www.thecalculatorsite.com/articles/units/history-of-the-calculator.php)).  The goal of this project is to emulate a four-function calculator on the DE2-115 board. This is essentially an example of Register Transfer Level (RTL) design in which the overall funtionality is fairly simple to state: you perform. a sequence of computations by entering decimal numbers   and arithemtic operations on a numeric keypad and observe the results on a    numeric display (typically an LCD screen).
Emulating this functionality on the DE2-115 board poses a couple of challeneges.
·  Unless we connect a keypad to the board (future project!) we have to figure out a way of using the 4 push-buttonn keys and the slider switches to enter  numbers and operations.
·  Until we figure out how to use the LCD display (future project!) we must settle for displaying the results on the 7-segment HEX displays.
Preparation
·  Review the lectures on RTL design
(https://umich.instructure.com/courses/700375/pages/session-17-register-transfer-level-rtl- design)and Sequential Multiplication(https://umich.instructure.com/courses/700375/pages/session-19-sequential-multiplication)and use the included Verilog specifications for the Cash Register and Booth Multiplier projects to  practice debugging and verifying functional correctness using ModelSim.
·  Review the included starter and helper Verilog modules.
Design Specification
The calculator performs addition (+), subtraction (-), multipli代 写Lab 7: Four-Function CalculatorJava
代做程序编程语言cation (x),and quotient (/) operations on 11-bit two's complement integers (full-fledged division requires introducing floating- point numbers which are beyond the scope of EECS 270!)
I/O Interface
Figure 1 shows the datapth/control decomposition and the DE2-115 interface of the calculator.
·  Entering and displaying numbers: Signed-magnitude numbers, in the range [-1023,1023], can be entered using SW[10:0] and should be displayed on {HEX7, HEX6, HEX5, HEX4}.
Operation results should be displayed on {HEX3, HEX2, HEX1, HEX0}. Numbers outside the range [-999,999] should be displayed as  indicating "can't be displayed'.
·  Entering operations: The four arithmetic operations can be entered by pressing a pushbutton KEY with SW[17] set to 0. Refer to the mapping in Figure1.
·  Entering commands: Besides entering numbers, two KEYs are used to enter the following commands when SW[17] is set to 1:
。= (equals): Pressing KEY[3] displays the result of the operation on {HEX3, HEX2, HEX1, HEX0}.
。C (clear): Pressing KEY[0] clears the result display and returns the calculator to its initial state.
·  Overflow indicator: Overflow should be indicated by LEDG[8] if any operation result is
outside the range of 11-bit two's complement numbers, ie., [-1024,1028] (would have been better if this was a red LED because of its location between the HEX displays!)
The calculator uses the built-in 50MHz CLOCK_50 which may need to be slowed down, using theClock_Div module (https://umich.instructure.com/courses/700375/files/38114943?wrap=1)   (https://umich.instructure.com/courses/700375/files/38114943/download?download_frd=1) , to   eliminate potential timing errors.

Figure 1: Four-Function Calculator Interface and Datapath/Control Decomposition Operation



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
