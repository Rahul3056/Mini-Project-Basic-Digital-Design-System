###  Mini Project – Basic Digital Design System

**Concept Overview**  
In this mini project, we will combine various digital design elements—like combinational logic, sequential logic, and FSM concepts—to implement a complete working **Digital Locking System**. This project helps you integrate your knowledge from previous days and simulate a practical embedded digital application.

**Project Description**  
We will design a **4-bit passcode-based digital locking system**. A user inputs a 4-bit code through switches. The system checks the input against a preset passcode. If the input matches the preset code, the system generates an `unlock` signal. A clock signal is used to confirm input entry, and a reset is used to clear the state.

**Specifications**  
- **Inputs:**  
  - `clk`: Clock signal to latch input  
  - `rst`: Reset signal (active-high)  
  - `code_in[3:0]`: 4-bit code input from the user  
- **Output:**  
  - `unlock`: High if entered code matches stored passcode  
- **Stored passcode:** 4'b1011 (can be modified for complexity)

**Truth Table**  
| Code Input (`code_in`) | Match? | `unlock` Output |  
|------------------------|--------|------------------|  
| 0000                   | No     | 0                |  
| 1011                   | Yes    | 1                |  
| 1111                   | No     | 0                |  
| 0101                   | No     | 0                |  

**Design Logic & Explanation**  
The design logic uses a synchronous process that compares the input code with a stored value upon the rising edge of the clock. If the match is found, the `unlock` output is set to 1. If the reset is pressed, the `unlock` is cleared.

**Boolean Equation (conceptual)**  
Let `PASSCODE = 1011`. Then,  
`unlock = (code_in[3] & ~code_in[2] & code_in[1] & code_in[0])`  
This boolean expression checks for exact matching bits. However, in the Verilog model, this is handled via comparison.

**Practical Application**  
This kind of lock system is found in:
- Keypad-locked doors  
- Basic security systems  
- Electronic safe boxes  
- Basic authentication systems in embedded designs

**Possible Extensions**  
- Add a counter that disables input after 3 incorrect attempts  
- Add a 7-segment display to show feedback (e.g., “FAIL” or “OPEN”)  
- Replace fixed passcode with programmable memory  
- Add FSM to manage lock states (e.g., IDLE → ENTER → CHECK → OPEN)

**Conclusion**  
This mini project integrates both combinational and sequential elements and prepares you for FSMs and more complex memory-based digital systems.
