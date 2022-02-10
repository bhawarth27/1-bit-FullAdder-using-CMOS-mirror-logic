# Design of 1-bit FullAdder using SkyWater 130nm technology
The purpose of this Project is to implement the design of 1-bit CMOS FullAdder using eSim (An open-source Electronic Design Automation tool designed by FOSSEE Project team of Indian Institute of Technology Bombay) and SkyWater 130nm PDKs (Process Design Kit) sponsored by Google.
# Table of Contents:
# Introduction
This design here presents 1-bit full adder cell designed by using cmos mirror technique. Full adder circuit is one of the most widely used building block in all arithmetic and digital data processing systems. This circuit accepts two 1-bit inputs and produce two 1-bit outputs i.e. sum and cout. We use property of inversion and self-duality to design this circuit. Because nowadays we have to deal with huge bits of data, we can switch to more advanced adder architectures like RIPPLE CARRY, CARRY SKIP, CARRY SELECT, CARRY LOOK AHEAD etc
# Reference Circuit Diagram
![image](https://user-images.githubusercontent.com/35188692/153359364-68cf9227-0848-4628-9bec-0b0a450e4f55.png)
# Description
Transistor level implementation of full adder using cmos mirror logic uses 28 transistors out of which 14 are nmos and 14 are pmos. By using cmos mirror design we can save area of 12 transistors as compared to conventional cmos approach. If a function obeys both inversion and self-duality properties than we can mirror the nmos stack to pmos i.e. pull-up stack is symmetrical to pull-down, unlike opposite to pull-down stack in conventional cmos. By this approach we can reduce pmos stack size and can have equal rise andfall delays. Instead of realizing two functions independently we will use cout signal to generate sum signal. The fulladder circuit presented in this paper can be further used as a building block to generate a N-bit adder, which accepts two n-bit inputs and produces n-bit sum. One such adder architecture is known as ripple carry adder where these fulladder blocks are cascaded one after the other. Each fulladder in this architecture produces 1-bit sum and pass the carry to the subsequent full adder. In this way carry ripples through each of the full adder stages. Speed of this carry rippling through each stages define the speed of the adder.Nowadays there are some advance static cmos techniques like-CPL, TG, GDI etc., to design a high speed and low power consumption full adder but tuning the circuit alone is not the feasible solution as we have to deal with huge bits of data at a time. In this case optimizing the architecture of the adder circuit can come in handy.
# eSim EDA Tool
eSim is an open source EDA tool for circuit design, simulation, analysis and PCB design, developed by FOSSEE Team at IIT Bombay. It is an integrated tool build using open source softwares such as KiCad, Ngspice and GHDL
# Features:
* An open-source EDA tool
# Google SkyWater 130nm PDK
![image](https://user-images.githubusercontent.com/35188692/153363448-8f46a3ac-9dc2-4ad1-a9e0-0840cbb045d2.png)
More details about this can be found [here](https://github.com/google/skywater-pdk)
# Schematic Diagram
![image](https://user-images.githubusercontent.com/35188692/153365348-d2fc4588-18de-438f-b387-e1efa6ba9f0b.png)
Modified Spice Netlist for write operation with Sky130 models, here `sky130_fd_pr__pfet_01v8` represents P channel mosfet and `sky130_fd_pr__nfet_01v8` represents N channel mosfets.
```
* /home/bhawarth/esim-workspace/attempt_1/attempt_1.cir
 .lib "sky130_fd_pr/models/sky130.lib.spice" tt
 xm2 net-_m2-pad1_ a vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm5 net-_m2-pad1_ b vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm9 net-_m10-pad3_ a vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm4 net-_m10-pad1_ cin net-_m2-pad1_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm10 net-_m10-pad1_ b net-_m10-pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm3 net-_m10-pad1_ cin net-_m1-pad1_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm1 net-_m1-pad1_ a gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm6 net-_m1-pad1_ b gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm7 net-_m10-pad1_ b net-_m7-pad3_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm8 net-_m7-pad3_ a gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm12 net-_m12-pad1_ a vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm15 net-_m12-pad1_ b vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm17 net-_m12-pad1_ cin vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm16 net-_m13-pad1_ net-_m10-pad1_ net-_m12-pad1_ vdd sky130_fd_pr__pfet_01v8 w=1
l=0.5
xm22 net-_m22-pad1_ b vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm23 net-_m23-pad1_ a net-_m22-pad1_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm24 net-_m13-pad1_ cin net-_m23-pad1_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm13 net-_m13-pad1_ net-_m10-pad1_ net-_m11-pad1_ gnd sky130_fd_pr__nfet_01v8
w=0.42 l=0.5
xm11 net-_m11-pad1_ a gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm14 net-_m11-pad1_ b gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm18 net-_m11-pad1_ cin gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm19 net-_m13-pad1_ cin net-_m19-pad3_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm20 net-_m19-pad3_ a net-_m20-pad3_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm21 net-_m20-pad3_ b gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm27 sum net-_m13-pad1_ vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm25 sum net-_m13-pad1_ gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
xm28 cout net-_m10-pad1_ vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5
xm26 cout net-_m10-pad1_ gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5
v1 a gnd pulse(0 1.8 0s 0s 0s 7us 14us)
v2 cin gnd pulse(0 1.8 0s 0s 0s 10us 20us)
v4 vdd gnd dc 1.8
* u5 cout plot_v1
* u3 cin plot_v1
* u4 sum plot_v1
* u1 a plot_v1
* u2 b plot_v1
v3 b gnd pulse(0 1.8 0s 0s 0s 5us 15us)
.tran 0.1us 20us
 * Control Statements 
.control
run
 plot v(cout)plot v(cin)
plot v(sum)
plot v(a)
plot v(b)
 .endc
 .end
```
