## Aim
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

## Apparatus Required
Vivado 2023.1
Computer system with a suitable operating system.

## Procedure

Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code:

Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.
Create the Testbench:

Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.
Add the Verilog Files:

Add both the design module and the testbench in the Vivado project.
Run Simulation:

Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs 0000 to 1001 (decimal 0 to 9).
Observe the Waveforms:

Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.
Save and Document Results:

Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

## Diagram
![image](https://github.com/user-attachments/assets/d7ecb419-906e-4e3b-9b82-f86ced4f364a)


## Verilog Code for Seven-Segment Display
```
// seven_segment_display.v
module sevensegment;
reg[3:0]bcd;
wire[6:0]seg;
sevensegment uut(.bcd(bcd),.seg(seg));
initial begin
bcd=4'b0000;
#2 bcd=4'b0000;
#2 bcd=4'b0001;
#2 bcd=4'b0010;
#2 bcd=4'b0011;
#2 bcd=4'b0100;
#2 bcd=4'b0101;
#2 bcd=4'b0110;
#2 bcd=4'b0111;
#2 bcd=4'b1000;
#2 bcd=4'b1001;
#2 $stop;
end
endmodule
```

OUTPUT: ![Seven segment 1](https://github.com/user-attachments/assets/5b7db640-33f6-457a-830e-8f26fffcf860)



## Testbench for Seven-Segment Display:
```

module multiplexer_tb;
  // Declare inputs as reg and outputs as wire
  reg s1, s0, a, b, c, d;
  wire y;

  // Instantiate the multiplexer module
  multiplexer uut (
    .s1(s1), 
    .s0(s0), 
    .a(a), 
    .b(b), 
    .c(c), 
    .d(d), 
    .y(y)
  );

  // Test cases
  initial begin
    // Monitor changes in inputs and output
    $monitor("s1 = %b, s0 = %b, a = %b, b = %b, c = %b, d = %b, y = %b", s1, s0, a, b, c, d, y);
    
    // Apply test vectors
    s1 = 0; s0 = 0; a = 1; b = 0; c = 0; d = 0; #10;  // Test case 1
    s1 = 0; s0 = 1; a = 0; b = 1; c = 0; d = 0; #10;  // Test case 2
    s1 = 1; s0 = 0; a = 0; b = 0; c = 1; d = 0; #10;  // Test case 3
    s1 = 1; s0 = 1; a = 0; b = 0; c = 0; d = 1; #10;  // Test case 4
    
    // Finish simulation
    $finish;
  end
endmodule
```

OUTPUT: ![testbench for seven segment](https://github.com/user-attachments/assets/7cc02851-fa5a-4b62-a4d0-ecc71eda76ac)


## Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs. This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
