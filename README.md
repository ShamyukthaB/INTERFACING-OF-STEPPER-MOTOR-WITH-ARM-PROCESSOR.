# INTERFACING-OF-STEPPER-MOTOR-WITH-ARM-PROCESSOR.
# Aim:
To write an embedded c program to interface STEPPER MOTOR with ARM processor LPC1768.
# Components Required:
# Hardware:
ARM LPC 1768 
STEPPER MOTOR.
# Software:
KEIL MICRO VISION 4.0 IDE
# Procedure:
⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.

⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.

⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.

⮚	Type the code.
 
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.

⮚	Build the project and fix the compiler errors/warnings if any.

⮚	Code is compiled with no errors. The .bin file is still not generated.

⮚	Right Click on Target Options to select the option for generating .bin file.

⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin

⮚	in c/c++ → include paths → desktop (00-libfiles).

⮚	.Bin file is generated after a rebuild.

⮚	Check the project folder for the generated .Bin file.

ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# Pin Diagram
<img width="468" height="303" alt="image" src="https://github.com/user-attachments/assets/46f8caaf-d0e2-4c7d-9e37-a36cdd5fc39b" />

# Circuit Diagram:
<img width="330" height="290" alt="image" src="https://github.com/user-attachments/assets/c522a456-fc1d-4c66-b0ed-2b1c2c58269e" />

# Program:
#include<lpc17xx.h> #include "gpio.h" #define pin1 20
#define pin2 21
#define pin3 22
#define pin4 23
#define control LPC_GPIO1-
>FIOPIN
void cmotor1()
{
control |=(1<<pin1); control |=(1<<pin2); control &=~(1<<pin3); control &=~(1<<pin4);

}
void cmotor2()
{
control &=~(1<<pin1); control |=(1<<pin2); control |=(1<<pin3); control &=~(1<<pin4);

}
void cmotor3()
{
control &=~(1<<pin1); control &=~(1<<pin2); control |=(1<<pin3); control |=(1<<pin4);
 
}

void cmotor4()
{
control |=(1<<pin1); control &=~(1<<pin2); control &=~(1<<pin3); control |=(1<<pin4);
}
void delay_ms(unsigned int ms)
{
unsigned int i,j;

for(i=0;i<ms;i++) for(j=0;j<20000;j++);
}
int main()
{
SystemInit();
//Clock and PLL configuration LPC_PINCON->PINSEL3 = 0x000000;
LPC_GPIO1->FIODIR
=(1<<pin1)|(1<<pin2)|(1<<pin3)
| (1<<pin4); while(1)
{
cmotor1(); delay_ms(50); cmotor2();

delay_ms(50);
cmotor3();

delay_ms(50);
cmotor4();

delay_ms(50);
}
}

# Output:
<img width="865" height="185" alt="image" src="https://github.com/user-attachments/assets/6f44734e-a66f-4fda-82fe-2f516f71ba53" />

Interfacing STEPPER MOTOR with ARM LPC 1768 is verified
<img width="789" height="421" alt="image" src="https://github.com/user-attachments/assets/77225360-e23b-49a4-b54a-2d501041de6c" />

# Result:
Thus interfacing STEPPER MOTOR with ARM processor LPC1768 is verified.
