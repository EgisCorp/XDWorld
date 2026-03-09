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

- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.
- $\color{red}{2.24.0\ 버전\ 배포는\ 3월\ 9일에\ 진행될\ 예정입니다.}$


### 2.24.0 (2026/03/09)
#### 1. JSPipe `setRadius` API 추가
- 파이프의 반경을 변경하는 API가 추가되었습니다.
  ```javascript
  var pipe = Module.createPipe("MY_PIPE");
  // pipe.create(...);
  pipe.setRadius(10.0);
  ```
  
#### 2. Module.getDataVisualizer API 생성 시 오류 수정
  * Module.getDataVisualizer를 통해 객체 생성 중 회전 각도가 잘못 적용되는 현상을 수정하였습니다. ([이슈 #547](https://github.com/EgisCorp/XDWorld/issues/547))

#### 3. JSPolygon 좌표 순서에 따른 컬링 오류 수정
  * setCoordinates(), setPartCoordinates() 함수에서 좌표의 순서가 반대로 들어온 경우에도 정상적으로 컬링이 되도록 수정하였습니다.

#### 4. 객체 선택 효과 변경
  * 기존 빨간색 반투명 효과를 홀로그램 효과로 변경하였습니다.<br>
https://github.com/user-attachments/assets/6686355e-3896-4f2f-ac1f-5c72e66f8ed4

### 2.24.0 (2026/03/09)
#### 1. Added `setRadius` API to JSPipe
* An API has been added to change the radius of a pipe.
  ```javascript
  var pipe = Module.createPipe("MY_PIPE");
  // pipe.create(...);
  pipe.setRadius(10.0);
  ```

#### 2. Fixed error when creating objects with Module.getDataVisualizer
* Fixed an issue where rotation angles were applied incorrectly when creating objects through Module.getDataVisualizer. ([Issue #547](https://github.com/EgisCorp/XDWorld/issues/547))

#### 3. Fixed culling error caused by JSPolygon coordinate order
* Fixed an issue where culling did not work correctly when coordinates were provided in reverse order in the setCoordinates() and setPartCoordinates() functions.

#### 4. Changed object selection effect
* The previous red translucent effect has been replaced with a hologram effect.<br>
https://github.com/user-attachments/assets/6686355e-3896-4f2f-ac1f-5c72e66f8ed4

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
