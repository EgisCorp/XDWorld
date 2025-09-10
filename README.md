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
- $\rm{\color{red}●\ 2.19.0\ 버전\ 업로드는\ 추석\ 연휴로\ 인해\ 둘째\ 주\ 월요일(10/13)에\ 배포\ 예정입니다.}$
- $\rm{\color{red}●\ Due\ to\ the\ Chuseok\ holiday,\ the\ 2.19.0\ release\ is\ scheduled\ for\ deployment\ on\ Monday,\ October\ 13\ (second\ week).}$
### 2.18.0 (2025/09/01)
#### 1. 오브젝트 선택 시 외곽선 렌더링
  * JSReal3D, JSGhostSymbol, JSPolygon 오브젝트 선택 시 아래 이미지와 같이 외곽선이 함께 출력됩니다.
    <img width="1424" height="649" alt="image" src="https://github.com/user-attachments/assets/c9c2aec6-b6d5-4a9b-9da4-5517201b9c43" />

  * JSOption의 setRenderSelectSilhouette API를 활용하여 외곽선을 끄고 켤 수 있습니다.
    ``` javascript
    Module.getOption().setRenderSelectSilhouette(true);   // on
    Module.getOption().setRenderSelectSilhouette(false);  // off
    ```

#### 2. DEM 단독 렌더링
  * 지형 영상 없이 DEM 단독으로 렌더링이 가능하도록 개선되었습니다.

#### 3. 화면 중심 기반 마우스 틸트, 회전 옵션 [(이슈 509)](https://github.com/EgisCorp/XDWorld/issues/509)
  * 마우스로 화면 틸트, 회전 시 화면 중앙점을 중심으로 움직이도록 옵션이 추가되었습니다.
    ``` javascript
    Module.getControl().setMouseClickCenterMode(true);
    ```

### 2.18.0 (2025/09/01)
#### 1. Outline Rendering on Object Selection

* When selecting **JSReal3D**, **JSGhostSymbol**, or **JSPolygon** objects, an outline is displayed as shown in the image below.
  <img width="1424" height="649" alt="image" src="https://github.com/user-attachments/assets/4eeb14bd-5da9-433e-bfc8-a4ff2cbc6e01" />


* You can toggle the outline on and off using the `setRenderSelectSilhouette` API in **JSOption**.

  ```javascript
  Module.getOption().setRenderSelectSilhouette(true);   // on
  Module.getOption().setRenderSelectSilhouette(false);  // off
  ```

#### 2. DEM-Only Rendering

* Improved to allow rendering of DEM without terrain imagery.

#### 3. Mouse Tilt & Rotation Based on Screen Center [(Issue 509)](https://github.com/EgisCorp/XDWorld/issues/509)

* Added an option to make mouse tilt and rotation operations move around the screen center point.

  ```javascript
  Module.getControl().setMouseClickCenterMode(true);
  ```



## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
