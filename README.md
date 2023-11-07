```
Name: Vanitha S
Register Number: 212222100057
```
# EXPERIMENT-02 INTEFACING A DIGITAL INPUT TO ARM DEVELOPMENT BOARD
## Aim: 
To Interface a Digital Input  (userpush button  ) to ARM   development board and write a  program to obtain  the data and flash the led  
## Components required:
STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

 
  
## Procedure:
Open a new STM32 Project

Selecting GPIO Ports

PA5 -> GPIO Output

PC13 -> GPIO Input

Configure the PC13 Port at Pull up Mode

Generate the code

Write the function(Declare,Define,Call)

Bulid Debug

Connect the ARM board to usb

Check for execution of the output using run option

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
