# 1802sim
Simulator for the RCA COSMAC CDP1802 Microprocessor

FEATURES
========
- View and Edit contents of all processor registers.
- Load/Save any memory block from/to a file in Intel Hex format (.hex), "memory dump" format (.rom), or raw binary (.bin) (i.e most EPROM burners e.g TL866).
  Note the .rom file format is a text file formatted as   :<address> <byte1> <byte2> ... <byte16><CR+LF> etc..  for example  :0000 71 00 f8 00 b3 f8 09 a3 d3 c0 02 92 f8 01 b6 f8
- View and Edit memory contents (in hex).
- Configurable ROM areas are coloured pale red in the memory display. Cannot be written to by the sim, but can still be edited by the user.
- Trace log shows run instruction history (disabled by checkbox, for greatly increased performance).
- Multiple Breakpoints can be set by either Address or Register Value.
- Single Step through running code.
- Serial Terminal. Configurable for 2400/9600 bps, 7/8 bits, Start Bit, Invert/not Q.  Supports Membership Card monitor and "Cenker" RCA Basic3.
 Transmits on Q and receives on EF3 or EF4. It is asynchronous, so it operates like a UART. The serial inbound character queue is visible to the user.
- Windows 7, Windows 10 (tested on both).  Requires .NET framework.
- High-DPI support (Renders nicely, tested on QHD/WQHD 13" laptop. No fuzziness or overlaid fields)
- I/O Bus current state and history trace shows INP and OUT interactions.
- Significant performance enhancements in Run mode (full speed). Now runs several times faster than previous version.
- Various fixes and improvements to register editing, IDLe mode, interrupt support, execution tracing etc..
- Improved execution tracing vs. performance.


Current v1.4.0.0 May 2021: Fixed some bugs! Added new Serial Terminal parameters. Now runs "Cenker" RCA Basic3 v1.1 and Chuck Yakym's Membership Card Monitor. Details below.
v1.3.3.0 August 2020: Added raw binary (.bin) to the options for memory load/save from/to a file. Prompts for load address. Thanks to Bob.
v1.3.1.0 June 2020: Fixed bug when loading (and saving) some Intel Hex files; Thanks to Kosmas.
v1.2.1.2 October 2019: Fixed some register issues; Thanks to Andy and Jeff.

Video about 1802 testing by Hey Birt! Includes a look at this 1802 simulator. Much thanks to Jeff - watch the video at https://www.youtube.com/watch?v=XPwuwjtjXnk&t=2s 
  
Configuring Serial Terminal
===========================
  
If you want to run RCA Basic3 v1.1 (originally written by Ron Cenker) and/or Chuck Yakym's MCSMP Membership Card Super Monitor Program, then follow the steps below.
You can get Chuck's monitor and RCA Basic3 by Ron Cenker at http://www.sunrise-ev.com/1802.htm Scroll down to the software section and look for MCSMP20.bin and/or MCBASIC3.bin

1. Start 1802sim, File -> Load Memory, choose Binary (*.bin), select the binary file to load.
2. Enter the load address (e.g RCA Basic3 by itself; MCBASIC3.bin at 0000, or Chuck's monitor MCSMP20.bin at 8000)
3. If you're loading Chuck's monitor, then edit memory locations 0000 and 0001 with contents C0, 80 respectively (i.e LBR 8000 jump to the monitor on boot)
4. Uncheck Execution Trace to get best performance.
5. Options -> Serial Terminal
6. Set the terminal options to Echo unchecked, 9600, 8 bits, Start Bit checked, InvertQ unchecked, Receive Line EF3 (all shown below)
7. Select radio button Run
8. Click onto the terminal window to focus it, and press Enter, you should see the prompt for the program you're running.
