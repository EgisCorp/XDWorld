[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation
  * [Korean] https://egiscorp.gitbook.io/xdworld-webgl-manual
  * [English] https://egiscorp.gitbook.io/xdworld_global_manual
### Demos & Sandbox - https://sandbox.egiscloud.com

# Introduction

> XDWORLD ENGINE, a 3D GIS engine based on WebGL

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## Features
-   웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
-   멀티 OS, 브라우저, No-Plugin 지원
-   3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
-   거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
-   다양한 도시계획 시뮬레이션 및 분석 기능 제공
-   공간정보 오픈플랫폼(V World) 데이터 서비스 가능
<br>

-   Supports 3D rendering based on web standard technologies HTML5 and WebGL
-   Multi OS, browser, and No-Plugin support
-   Provides a variety of JavaScript web APIs for 3D spatial data web developers
-   Offers basic 3D analysis functions such as distance, area, and volume calculations
-   Provides various urban planning simulation and analysis features
-   Capable of spatial information open platform (V World) data services

## Fields

-   GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등
(GIS, Urban Information Systems, Location-Based Services, Facility Management, Perspective Views, Site Analysis, Terrain Analysis, Urban Planning, Construction Site Management, and Agricultural Land Management.)

## Update

### 2.4.0 (2024/6/28)

#### 1. 화면 분할 시 잔상이 남는 현상 수정
  * 지형 투명도 조절과 함께 화면 분할 기능 사용 시 분할 화면에 잔상이 남는 현상을 수정하였습니다.
  * 화면 분할 기능 사용 시 레이어 배치 방향이 반대로 보이는 점을 확인하여 수정하였습니다.

#### 2. Camera Quake의 진동 오류 수정
  * Camera Quake(카메라 흔들림)기능에서, 진동 주기가 초단위로 적용되는 오류를 수정하였습니다.

#### 3. JSFlowPolygon 객체 색상 설정 오류 수정
  * create API 실행 전 color 속성 설정 시 값이 정상적으로 반영되지 않는 현상을 수정하였습니다.

#### 4. 전광판, 비디오 객체 기능 개선 
  * 사용자 편의성을 위해 객체 생성 이후의 기능들 엔진 내부에 삽입 및 속도개선되었습니다.
  * 기존 비디오 텍스쳐 관련 기능은 2024년까지 지원합니다.
  * 새로운 사용법은 [비디오텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=object_video)를 참고하시기 바랍니다.

#### 5. WMS 로딩 방식 선택
  * 사용자의 통신 환경과 WMS 및 하이브리드 상태에 따라 선택 가능 하도록 하는 API 추가
  ``` javascript
  // Default : 0
  //Module.getOption().setHybridRenderType(0);   // 기존과 동일
  Module.getOption().setHybridRenderType(1);   // 변경된 순서에 따라 바로 반영
  ```

#### 6. 장해물 판별 기능 추가
 * 카메라와 JSPoint, JSHTMLObject 객체 사이에 장해물(지형, 시설물) 존재 시 가시화 유무를 설정하는 변수를 추가 하였습니다.
  ```javascript
  Module.getOption().object_ahead = 0; 기존 방식(장해물 미판정)
  Module.getOption().object_ahead = 1; 장해물에 따른 가시화 설정
  ```

#### 7. 카메라 좌/우 이동 API 추가
  * 카메라 이동 함수 moveLeftRight가 추가되었습니다.
  * 지정한 값 만큼 카메라가 좌/우 방향으로 이동합니다.
  ``` javascript
  Module.getViewCamera().moveLeftRight(0.01);
  Module.getViewCamera().moveLeftRight(-0.01);
  ```

#### 8. 레이어 화면 분할 렌더링 기능 오류 수정
  * 화면 분할 기능 사용 시 좌/우 방향이 반대로 적용되는 현상을 수정하였습니다.
  * 화면 분할 후 특정 화면에서 화면의 잔상이 남는 현상을 수정하였습니다 [이슈 #401](https://github.com/EgisCorp/XDWorld/issues/401)

### 2.4.0 (2024/6/28)

#### 1. Fixed Afterimage Issue When Splitting Screen
  * Fixed the issue where afterimages appeared on split screens when adjusting terrain transparency.
  * Corrected the reversed layer arrangement direction when using the screen split function.

#### 2. Fixed Vibration Error in Camera Quake
  * Corrected the error where the vibration period in the Camera Quake (camera shake) function was applied in seconds.

#### 3. Fixed Color Setting Error for JSFlowPolygon Object
  * Fixed the issue where the color property was not properly applied when set before executing the create API.

#### 4. Improved LedBoard and Video Object Functions
  * For user convenience, functionalities after object creation have been integrated into the engine for improved speed.
  * Existing video texture-related features will be supported until 2024.
  * Please refer to the [video texture](https://sandbox.egiscloud.com/code/main.do?id=object_video) for the new usage instructions.

#### 5. Added WMS Loading Method Selection
  * Added an API to allow selection based on the user's communication environment and WMS and hybrid status.
  ```javascript
  // Default: 0
  // Module.getOption().setHybridRenderType(0);   // Same as before
  Module.getOption().setHybridRenderType(1);   // Immediately applied according to the new order
  ```

#### 6. Added Obstacle Detection Feature
 * Added a variable to set the visibility based on the presence of obstacles (terrain, facilities) between the camera and JSPoint or JSHTMLObject objects.
  ```javascript
  Module.getOption().object_ahead = 0; // Existing method (no obstacle detection)
  Module.getOption().object_ahead = 1; // Visibility setting based on obstacles
  ```

#### 7. Added Camera Left/Right Movement API
  * Added the moveLeftRight function for camera movement.
  * Moves the camera left or right by the specified value.
  ```javascript
  Module.getViewCamera().moveLeftRight(0.01);
  Module.getViewCamera().moveLeftRight(-0.01);
  ```

#### 8. Fixed Layer Screen Split Rendering Issue
  * Fixed the issue where the left/right direction was applied in reverse when using the screen split function.
  * Fixed the issue where afterimages remained on specific screens after splitting the screen [Issue #401](https://github.com/EgisCorp/XDWorld/issues/401)

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
