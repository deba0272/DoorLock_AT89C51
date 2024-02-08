# DoorLock_AT89C51
Some important parts are explained....
#include<reg51.h>
This line includes the header file "reg51.h" which contains definitions specific to the 8051 microcontroller.
sbit RS = P3^0;
sbit EN = P3^1;
sbit IN1 = P3^2;
sbit IN2 = P3^3;
These lines declare bit-addressable variables RS, EN, IN1, and IN2, representing the control pins of the LCD and some motor control pins. They are mapped to specific bits of Port 3 on the 8051 microcontroller.
void cmd(char cm)
{
	P2 = cm;
	RS = 0;
	EN = 1;
	delay(1);
	EN = 0;
}
This function sends a command cm to the LCD. It sets the data port (P2) to the command value, sets the RS (Register Select) pin low to indicate that a command is being sent, sets the EN (Enable) pin high to enable the LCD, introduces a delay, and then sets the EN pin low to disable the LCD.
void lcdint()
{
	cmd(0x01);
	cmd(0x38);
	cmd(0x0E);
	cmd(0x80);
}
This function initializes the LCD. It sends a series of commands to the LCD to set it up for 4-bit mode, two-line mode, and to position the cursor at the beginning of the first line.
