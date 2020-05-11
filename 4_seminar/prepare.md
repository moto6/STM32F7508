## 수업전
  - 준비물 : STM32F7508 보드, Mini-USB to USB, Micro-USB to USB(각1개씩)
  - 설치 프로그램 
    - CubeMX
    - Truestudio
    - CubeF7 MCU Pack
    - Cube Programmer

## toggle LED 하기
  - LED(LD1, Green색상) 약 100ms 마다 점멸동작
  - 약 200번째 라인
    ```c
        /* USER CODE BEGIN RTOS_THREADS */
        /* add threads, ... */
        /* USER CODE END RTOS_THREADS */

        /* Start scheduler */
        //osKernelStart();이부분을 꼭 주석처리 해주세요
        
        /* We should never get here as control is now taken by the scheduler */
        /* Infinite loop */
        /* USER CODE BEGIN WHILE */
        while (1)
        {

            /* USER CODE END WHILE */

            /* USER CODE BEGIN 3 */
            //아래 두줄을 타이핑
            HAL_GPIO_TogglePin (GPIOI,GPIO_PIN_1);
            HAL_Delay(100);        

        }
        /* USER CODE END 3 */
        }

    ```
  - CubeMX에서 PI1 검색 후 "GPIO OUT"으로 설정 변경


## toggle LED with SW
  - 스위치(B1, 파란색)가 눌린 동안에만 LED가 켜져 있습니다.
  - 약 200번째 라인
    ```c
        
    /* Start scheduler */
    //osKernelStart();
    
    /* We should never get here as control is now taken by the scheduler */
    /* Infinite loop */
    /* USER CODE BEGIN WHILE */

    while (1)
    {
        /* USER CODE END WHILE */

        /* USER CODE BEGIN 3 */
        if(HAL_GPIO_ReadPin(GPIOI,GPIO_PIN_11) == 1) {
            HAL_GPIO_WritePin(GPIOI,GPIO_PIN_1,1);
        }
        else {
            HAL_GPIO_WritePin(GPIOI,GPIO_PIN_1,0);
        }
    ```


## UART 출력
  - uart로 uart 출력
    ```c
        /* Start scheduler */
        //osKernelStart();
        
        /* We should never get here as control is now taken by the scheduler */
        /* Infinite loop */
        /* USER CODE BEGIN WHILE */
        char mystr[] = "hello world!\n\r";
        HAL_UART_Init(&huart1);
        while (1)
        {
            /* USER CODE END WHILE */


            /* USER CODE BEGIN 3 */

            HAL_UART_Transmit(&huart1,mystr,sizeof(mystr),1000);
            HAL_Delay(100);

        }
        /* USER CODE END 3 */
        }
    ```

## TIMER 사용 
- 
- 
  - 코드
  ```c
    /* USER CODE END 2 */

    /* Infinite loop */
    /* USER CODE BEGIN WHILE */
    HAL_TIM_Base_Start_IT(&htim7);
    HAL_TIM_Base_Start_IT(&htim6);
    char mystr[] = "hello world!\n\r";
    HAL_UART_Init(&huart1);
    while (1)
    {
        /* USER CODE END WHILE */

        /* USER CODE BEGIN 3 */

    }
    /* USER CODE END 3 */
    }
  ```
  - file : stm32f7xx_it.c
  ```c
    
    /* USER CODE BEGIN 1 */
    void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
    {
        char mystr1[] = "7777TIM7 MESG!!\n\r";
        char mystr2[] = "TIM6 MESG!!\n\r";

        if(htim = TIM7) {
            HAL_UART_Transmit(&huart1,mystr1,sizeof(mystr1),100);

        }

        if(htim = TIM6) {
            HAL_UART_Transmit(&huart1,mystr2,sizeof(mystr2),100);
        }



    }

    /* USER CODE END 1 */
  ```