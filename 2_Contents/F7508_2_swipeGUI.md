# 
## 2. STM32F7508-Discovery Swipe GUI 만들기  
  - [목차로 돌아가기](https://github.com/d-h-k/STM32F7508#%EB%AA%A9%EC%B0%A8-index)
 ### 설치가 필요한 것
  - [ST-LINK 설치 필수 !!!](https://my.st.com/content/my_st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-programmers/stsw-link004.license=1563552768058.product=STSW-LINK004.version=4.5.0.html)
 ### 참고영상 -  TOUCHGFX, STM
  - [TOUCHGFX 유툽 동영상](https://www.youtube.com/watch?time_continue=17&v=X20f1ag2x4Q)
  - [TOUCH GFX 유툽 체널](https://www.youtube.com/channel/UCPmAQbY9KbHqdQ_GwUGg1bA)
  - [STMicro사 유툽 체널](https://www.youtube.com/user/STonlineMedia)
 ### 실습결과 
  - [결과물 동영상 1 - 전자공작 카페](https://cafe.naver.com/circuitsmanual/213572) 
  - [결과물 동영상 2 - 전자공작 카페](https://cafe.naver.com/circuitsmanual/213571)
 ### 요구조건
   ```
    [퀘스트 2]
    1.TouchGFX를 이용해서 STM32F7508-DK보드상 LCD에 화면전환(screen swipe) 을 구현해보세요.
    2.터치스크린의 Swipe 동작시 두개 이상의 화면(윈도우)이 슬라이드 방식으로 화면전환되는 효과 구현.

    [퀘스트 통과 조건]
    1.보드에서의 동작을 녹화한 동영상을 “퀘스트2 (7.22~7.28)” 게시판에 올려주세요.
    2.글 작성 시 (소스파일을 프로젝트 폴더째) 압축해서 첨부합니다.
    3.작성한 글을 파일로 인쇄해서 PDF 파일로 저장합니다.
    4.상기 PDF파일 및 압축파일을 카페매니저 메일 @@@(보안상 가림) 으로 발송합니다.
    5.메일 발송하는 파일명에는 퀘스트번호 및 카페 별명을 추가해주세요

    [단계]
    1.TouchGFXDesigner에서 프로젝트 생성
    두개 이상의 Window를 생성하고 Swipe화면전환 기능 구현
    2.완료된 프로젝트를 Simulator 를 통해 확인
    3.완성된 프로젝트를 STM32F7508-DK 디스커버리 보드에 [Run Target] 버튼을 클릭하여 다운로드 합니다.
    4.다운로드 완료 및 디스커버리보드에서 실행
   ```
 #
 ## 따라하기
- TouchGFX 를 실행 후 Simulaotr 에서 Change버튼을 클릭합니다
- ![](../img/20190724-no002.png)
- STM32F750 Discovery 를 선택합니다
- ![](../img/20190724-no003.png)
- Blank UI 버튼을 클릭합니다
- ![](../img/20190724-no004.png)
- Swipe ... Example 버튼을 클릭합니다
- ![](../img/20190724-no005.png)
- SELECT 버튼을 클릭
- ![](../img/20190724-no006.png)
- CREATE 버튼을 클릭하여 프로젝트를 생성
- ![](../img/20190724-no007.png)
- 매번 뜨는 경고창입니다 Yes버튼을 눌러서 진행
- ![](../img/20190724-no008.png)
- 첫 화면에서 빨간색 박스 속 Text를 변경합니다 
- 저는 
- ![](../img/20190724-no009.png)
- 
- ![](../img/20190724-no010.png)
- 
- ![](../img/20190724-no011.png)
- 
- ![](../img/20190724-no012.png)
- 
- ![](../img/20190724-no013.png)
- 
- ![](../img/20190724-no014.png)
- 
- ![](../img/20190724-no015.png)
- 
- ![](../img/20190724-no016.png)
- 
- ![](../img/20190724-no017.png)
- 
- ![](../img/20190724-no018.png)
- 
- ![](../img/20190724-no019.png)
- 
- ![](../img/20190724-no020.png)
- 
- ![](../img/20190724-no021.png)
- 
- ![](../img/20190724-no022.png)
- 
- ![](../img/20190724-no023.png)
- 
- ![](../img/20190724-no024.png)
- 
- ![](../img/20190724-no025.png)
- 
- ![](../img/20190724-no026.png)
- 
- ![](../img/20190724-no027.png)
- 
- ![](../img/20190724-no028.png)
- 
- ![](../img/20190724-no029.png)
