# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
/* write all the steps invloved */



### PROGRAM 
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: ARAVIND SAMY.P
RegisterNumber:212222230011
### UP COUNTER:

module sync(clk,t);
input clk;
output reg [0:2]t;
always@ (posedge clk)
begin
t[2]=((t[1]&t[0])^t[2]);
t[1]=t[0]^t[1];
t[0]=1^t[0];
end
endmodule

### DOWN COUNTER:
module sync(clk,t);
input clk;
output reg [0:2]t;
wire bar2,bar1,bar0;
not(bar2,t[2]);
not(bar1,t[1]);
not(bar0,t[0]);
always@ (posedge clk)
begin
t[2]=((bar1&bar0)^t[2]);
t[1]=bar0^t[1];
t[0]=1^t[0];
end
endmodule
*/






### RTL LOGIC UP COUNTER AND DOWN COUNTER  
### UP COUNTER:

![UP RTL](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/8eb088cc-f63c-4b0b-92b2-b6a47d8978e8)

### DOWN COUNTER:


![DOWN RTL](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/d9df028e-1f07-4352-8be8-17220d0cbbc6)



### TIMING DIGRAMS FOR COUNTER  
### UP COUNTER:
![UP TIMI](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/6bce420b-0dff-4b9d-94e4-88ae4637da51)


### DOWN COUNTER:

![DOWN TIMI](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/88f57263-f995-46de-9ebb-4d5ef8bc9ab8)



### TRUTH TABLE 
### UP COUNTER:
![UP TRUTH](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/bcf6e401-a332-4af5-99b4-916971c91b33)


### DOWN COUNTER:


![DOWN TRUTH](https://github.com/Aravindsamy04/Exp-7-Synchornous-counters-/assets/113497037/32d17096-25e7-4b30-a2cf-f7318e423fb0)


### RESULTS :
Thus, 4 bit up and down counters are implemented and its functionality is validated successfully.


