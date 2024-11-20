# 4-bit-Ripple-Carry-Adder-using-Task-and-4-bit-Ripple-Counter-using-Function-with-Testbench
# Aim:
To design and simulate a 4-bit Ripple Carry Adder using Verilog HDL with a task to implement the full adder functionality and verify its output using a testbench.
To design and simulate a 4-bit Ripple Counter using Verilog HDL with a function to calculate the next state and verify its functionality using a testbench.

# Apparatus Required:
Computer with Vivado or any Verilog simulation software.
Verilog HDL compiler.

// Verilog Code ripple counter
```
module ripple_counter_4bit (
input clk,           
input reset,        
output reg [3:0] Q   
);
function [3:0] next_state;
    input [3:0] curr_state;
    begin
        next_state = curr_state + 1;
    end
endfunction
always @(posedge clk or posedge reset) begin
    if (reset)
        Q <= 4'b0000;       // Reset the counter to 0
    else
        Q <= next_state(Q); // Increment the counter
end
endmodule
```
OUTPUT:
![image](https://github.com/user-attachments/assets/7dac18b3-030d-4eb6-bd49-ad380b92f81b)


// TestBench
```
module ripple_counter_4bit_tb;
reg clk;
reg reset;
wire [3:0] Q;
ripple_counter_4bit uut (
    .clk(clk),
    .reset(reset),
    .Q(Q)
);
always #5 clk = ~clk;
initial begin
    clk = 0;
    reset = 1;
    #20 reset = 0;
    #200 $stop;
end
initial begin
    $monitor("Time = %0t | Reset = %b | Q = %b", $time, reset, Q);
end
endmodule
```
OUTPUT:
![image](https://github.com/user-attachments/assets/1b4cc8c6-2b17-49fe-8e05-0c12a58fcff9)


# Conclusion:
The 4-bit Ripple Carry Adder was successfully designed and implemented using Verilog HDL with the help of a task for the full adder logic. The testbench verified that the ripple carry adder correctly computes the 4-bit sum and carry-out for various input combinations. The simulation results matched the expected outputs.

The 4-bit Ripple Counter was successfully designed and implemented using Verilog HDL. A function was used to calculate the next state of the counter.

