# Constraint Generation
> Clock & Input SDC Constraint Automation — VSDSYNTH

![Tool](https://img.shields.io/badge/Tool-TCL-blue)
![Format](https://img.shields.io/badge/Format-SDC-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Developed a **CSV-to-SDC translation engine** to automate complete clock and input constraint generation — parsing CSV timing data into industry-standard SDC commands.
- Engineered a **smart port parser** with dynamic RTL scanning to distinguish single-bit and bussed signals — validated end-to-end on the `openMSP430` design.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Clock Constraint Generation | CSV parsing, `create_clock` SDC generation, duty cycle calculation |
| Port Categorization | Single-bit vs bussed signal detection, namespace sanitization |
| Port Extraction & Normalization | Dynamic RTL scanning, space normalization, temporary file buffering |
| Bit & Bussed Differentiation | Dual-layer pattern matching, `set_input_delay`, `set_input_transition` |
| Input Constraint Generation | Algorithmic port matching, bus detection, SDC file population |

<h2>📝 Stage Details</h2>

**Task 1 — Automated Clock Constraint Generation** &nbsp;|&nbsp; `create_clock` `SDC` `Duty Cycle`

Developed a translation engine to convert CSV data into functional SDC commands. Implemented clock data parsing to extract Clock Name, Period, and duty cycle metadata from the internal design matrix. Generated `create_clock` commands with precise waveform definitions and automated SDC file creation in the design output hierarchy. Verified generated constraints against the CSV configuration.

**Task 2 — Port Categorization & Bus Expansion Logic** &nbsp;|&nbsp; `Regex` `Bus Detection` `Port Sorting`

Developed a smart port parser to distinguish single-bit signals from multi-bit buses using TCL regular expressions. Created a categorization engine separating ports into "Bussed" and "Bit" types for specialized constraint handling. Added namespace sanitization to format CSV-derived port names for proper netlist integration. Validated against the `openMSP430` netlist confirming correct identification of all primary inputs.

**Task 3 — Automated Port Extraction & Space-Normalization** &nbsp;|&nbsp; `RTL Scanning` `Regex` `Temp File Buffering`

Integrated dynamic RTL scanning to automatically extract all input port declarations from Verilog source files. Developed fixed-space reformatting routines to standardize whitespace and tabs for consistent parsing. Implemented automated data cleaning to strip Verilog keywords and delimiters, isolating pure signal names for constraint mapping.

**Task 4 — Bit & Bussed Port Differentiation Logic** &nbsp;|&nbsp; `Pattern Matching` `set_input_delay` `set_input_transition`

Implemented dual-layer pattern matching to verify CSV-defined constraints against the reformatted RTL port list. Developed automated SDC formatting routines for `set_input_delay`, `set_input_transition`, and `set_output_delay`. Engineered intelligent bus handling to apply constraints accurately to entire buses or individual bits. All constraints appended to a single master SDC file using standard `[get_ports]` syntax.

**Task 5 — Input Constraint Generation & Advanced Port Differentiation** &nbsp;|&nbsp; `get_ports` `Yosys` `OpenTimer`

Developed algorithmic port matching to link high-level constraints with RTL port declarations. Implemented intelligent bus detection to apply constraints to individual bits accurately. Validated flow scalability on the `openMSP430` design — all primary inputs constrained correctly without manual intervention.

<h2>🖼️ Implementation Results</h2>

### Automated Clock Constraint Generation
![1](1_Creating_complete_clock_constraints_1.png)
![2](1_Creating_complete_clock_constraints_2.png)
![3](1_Creating_complete_clock_constraints_3.png)
![4](1_Creating_complete_clock_constraints_4.png)
![5](1_Creating_complete_clock_constraints_5.png)
![6](1_Creating_complete_clock_constraints_6.png)

### Port Categorization & Bus Expansion Logic
![1](2_Algorithm_to_categorisze_input_ports_as_bits_and_bussed_1.png)
![2](2_Algorithm_to_categorisze_input_ports_as_bits_and_bussed_2.png)

### Automated Port Extraction & Space-Normalization
![1](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_1.png)
![2](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_2.png)
![3](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_3.png)
![4](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_4.png)
![5](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_5.png)
![6](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_6.png)
![7](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_7.png)
![8](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_8.png)
![9](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_9.png)
![10](3_Grepping_input_ports_from_all_verilog_and_reformatting_for_fixed_space_10.png)

### Bit & Bussed Port Differentiation Logic
![1](4_Bit_or_bussed_differentiation_1.png)
![2](4_Bit_or_bussed_differentiation_2.png)
![3](4_Bit_or_bussed_differentiation_3.png)
![4](4_Bit_or_bussed_differentiation_4.png)
![5](4_Bit_or_bussed_differentiation_5.png)
![6](4_Bit_or_bussed_differentiation_6.png)
![7](4_Bit_or_bussed_differentiation_7.png)
![8](4_Bit_or_bussed_differentiation_8.png)
![9](4_Bit_or_bussed_differentiation_9.png)
![10](4_Bit_or_bussed_differentiation_10.png)
![11](4_Bit_or_bussed_differentiation_11.png)
![12](4_Bit_or_bussed_differentiation_12.png)
![13](4_Bit_or_bussed_differentiation_13.png)

### Input Constraint Generation & Advanced Port Differentiation
![1](5_Input_constraint_generation_and_bits_or_buffed_differentiation_1.png)
![2](5_Input_constraint_generation_and_bits_or_buffed_differentiation_2.png)
![3](5_Input_constraint_generation_and_bits_or_buffed_differentiation_3.png)
![4](5_Input_constraint_generation_and_bits_or_buffed_differentiation_4.png)
![5](5_Input_constraint_generation_and_bits_or_buffed_differentiation_5.png)
![6](5_Input_constraint_generation_and_bits_or_buffed_differentiation_6.png)
![7](5_Input_constraint_generation_and_bits_or_buffed_differentiation_7.png)
![8](5_Input_constraint_generation_and_bits_or_buffed_differentiation_8.png)
![9](5_Input_constraint_generation_and_bits_or_buffed_differentiation_9.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 02 : CSV Parsing](../02%20:%20CSV%20Parsing) &nbsp;|&nbsp; [Next : 04 : Synthesis & Error Handling](../04%20:%20Synthesis%20%26%20Error%20Handling)
