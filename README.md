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

$\huge{\rm{\color{red}Important\ note}}$

$\rm{\color{red}●\ 1인칭\ 카메라\ 비디오\ 텍스쳐\ 기능\ 지원\ 중단}$
  * 기존 1인칭 카메라 비디오 텍스쳐 기능은 2025년까지 지원합니다. 
  * JSCamera 클래스의 삭제 API ---------> JSVideoObject 클래스의 대체 API 
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera 클래스의 삭제 property ---------> JSVideoObject 클래스의 대체 property</summary>
     
     - [x] videoStreaming ---------------> videoStreaming
     - [x] videoFar -----------------------> far
     - [x] videoFovX ---------------------> fovX
     - [x] videoFovY ---------------------> fovY
     - [x] videoAlpha --------------------> alpha
     - [x] videoAxisX --------------------> axisX
     - [x] videoAxisY --------------------> axisY
     - [x] videoZoom --------------------> zoom
     - [x] videoFarPlane -----------------> background
     - [x] videoResolution ---------------> resolution
     - [x] videoObjectMapping ---------> objectMapping
     - [x] videoIsplayer ------------------> isPlayer
   </details>

  * 비디오 객체  [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

$\rm{\color{red}●\ Discontinuation\ of\ First-Person\ Camera\ Video\ Texture\ Feature}$
  * The existing First-Person Camera Video Texture feature will be supported until 2025.
  * JSCamera class removal API ---------> Replacement API in JSVideoObject class
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera class removal properties ---------> Replacement properties in JSVideoObject class</summary>
     
     - [x] videoStreaming ---------------> videoStreaming
     - [x] videoFar -----------------------> far
     - [x] videoFovX ---------------------> fovX
     - [x] videoFovY ---------------------> fovY
     - [x] videoAlpha --------------------> alpha
     - [x] videoAxisX --------------------> axisX
     - [x] videoAxisY --------------------> axisY
     - [x] videoZoom --------------------> zoom
     - [x] videoFarPlane -----------------> background
     - [x] videoResolution ---------------> resolution
     - [x] videoObjectMapping ---------> objectMapping
     - [x] videoIsplayer ------------------> isPlayer
   </details>

  * Please refer to [Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video), [LED Board](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), and [RTT Video](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture).

## Update

- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.

### 2.17.0 (2025/08/11)
### 1. Figure 객체 편집 UI 제어 API 추가
  - scaleLock, rotateLock, moveLock
```javascript
let fig = Module.createFigure("figs");

// 크기 UI 삭제
fig.scaleUI = false;

// 회전 UI 삭제
fig.rotateUI = false;

// 이동 UI 삭제
fig.moveUI = false;
```

### 2. 하드웨어 가속 옵션 안내
  - Chrome 브라우저가 아닐 경우 Chrome 브라우저 권장 안내
    
    <img width="436" height="124" alt="image" src="https://github.com/user-attachments/assets/4f0f740c-4d97-44c1-a4f3-e8f9b00bbf2b" />


  - Chrome 브라우저의 "하드웨어 가속" or "그래픽 가속" 을 사용하지 않을 경우 안내
    
    <img width="497" height="283" alt="image" src="https://github.com/user-attachments/assets/56b44112-ee37-4ae9-b722-0164d397ed14" />


#### 3. Indicator 기능 개선
 * 타겟이 카메라 뒤에 있는 경우 Indicator가 정상적으로 계산되지 않는 현상을 수정하였습니다.

Sure! Here's the English translation of the release notes:
---
    
### 2.17.0 (2025/08/11)
### 1. Added API to control Figure object editing UI

* `scaleLock`, `rotateLock`, `moveLock`

```javascript
let fig = Module.createFigure("figs");

// Remove scale UI
fig.scaleUI = false;

// Remove rotation UI
fig.rotateUI = false;

// Remove movement UI
fig.moveUI = false;
```

### 2. Hardware acceleration guidance

* If the browser is not Chrome, display a recommendation to use Chrome.

  <img width="436" height="124" alt="image" src="https://github.com/user-attachments/assets/4f0f740c-4d97-44c1-a4f3-e8f9b00bbf2b" />

* If Chrome's "Hardware Acceleration" or "Graphics Acceleration" is disabled, display a notice.

  <img width="497" height="283" alt="image" src="https://github.com/user-attachments/assets/56b44112-ee37-4ae9-b722-0164d397ed14" />

### 3. Indicator feature improvements

* Fixed an issue where the indicator was not calculated correctly when the target was behind the camera.

---




## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
