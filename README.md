# EXPERIMENT-02 INTEFACING A DIGITAL INPUT TO ARM DEVELOPMENT BOARD
## Aim: 
To Interface a Digital Input  (userpush button  ) to ARM   development board and write a  program to obtain  the data and flash the led  
## Components required:
STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

 
  
## Procedure:
1. click on STM 32 CUBE IDE, the following screen will appear

<img src=https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png width=450 height=450>

2. click on FILE, click on new stm 32 project
 
<img src=https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png width=450 height=450>
<img src=https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png width=450 height=450>

3. select the target to be programmed  as shown below and click on next 

<img src=https://user-images.githubusercontent.com/36288975/226189280-ed5dcf1d-dd8d-43ae-815d-491085f4863b.png width=450 height=450>

4.select the program name 

<img src=https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png width=450 height=450>


5. corresponding ioc file will be generated automatically
 
<img src=https://user-images.githubusercontent.com/36288975/226189378-3abbdee2-0df6-470f-a3cd-79c74e3d3ad8.png width=450 height=450>

6.select the appropriate pins as gipo, in or out, USART or required options and configure 

<img src=https://user-images.githubusercontent.com/36288975/226189403-f7179f1a-3eae-4637-826b-ab4ec35ba1e1.png width=450 height=450>
<img src=https://user-images.githubusercontent.com/36288975/226189425-2b2414ce-49b3-4b61-a260-c658cb2e4152.png width=450 height=450>


7.click on cntrl+S , automaticall C program will be generated

<img src=https://user-images.githubusercontent.com/36288975/226189443-8b43451d-0b14-47e4-a20b-cc09c6ad8458.png width=450 height=450>
<img src=https://user-images.githubusercontent.com/36288975/226189450-85ffa969-2ffb-4788-81e5-72d60fdda0f1.png width=450 height=450>

8. edit the program and as per required

<img src=https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png width=450 height=450>

9. use project and build all
    
<img src=https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png width=450 height=450>

10. once the project is bulild 

<img src=https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png width=450 height=450>

11. click on debug option
    
<img src=https://user-images.githubusercontent.com/36288975/226189625-37daa9a3-62e9-42b5-a5ce-2ac63345905b.png width=450 height=450>

12. connect the  ARM board to power supply and usb 


13. check for execution of the output using run option 


## STM 32 CUBE PROGRAM :
```
#include "main.h"
#include "stdbool.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);
void push_button();
bool bstat;

int main(void)
{

  HAL_Init();


  MX_GPIO_Init();

  while (1)
  {
	  push_button();
  }

}

void push_button()
{
	bstat=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_13);
	if (bstat==0)
		HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_RESET);
	else
		HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_SET);
}



static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};

  __HAL_RCC_GPIOC_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);

  GPIO_InitStruct.Pin = GPIO_PIN_13;
  GPIO_InitStruct.Mode = GPIO_MODE_INPUT;
  GPIO_InitStruct.Pull = GPIO_PULLUP;
  HAL_GPIO_Init(GPIOC, &GPIO_InitStruct);

  GPIO_InitStruct.Pin = GPIO_PIN_5;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

}


void Error_Handler(void)
{

  __disable_irq();
  while (1)
  {
  }

}

#ifdef  USE_FULL_ASSERT

void assert_failed(uint8_t *file, uint32_t line)
{

}
#endif
```
## Output  :
 
 ### Switch off:
 <img src=https://github.com/Vanitha-SM/EXPERIMENT--02-INTEFACING-A-DIGITAL-INPUT-TO-ARM-DEVELOPMENT-BOARD/assets/119557985/b2957063-24e1-4857-a997-4d51b6262c53 width=450 height=450>
 
 ### Switch off:
 <img src=https://github.com/Vanitha-SM/EXPERIMENT--02-INTEFACING-A-DIGITAL-INPUT-TO-ARM-DEVELOPMENT-BOARD/assets/119557985/71d7468d-6898-45ad-88a2-c8714da2a3ba width=450 height=450>

## Result :
Interfacing a digital Input (Pushbutton ) with ARM microcontroller based IOT development is executed and the results are verified.
