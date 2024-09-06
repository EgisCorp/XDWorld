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

## Notice

### 비디오 텍스쳐 기능 개선
* 사용자 편의성을 위해 객체 생성 이후의 기능들 엔진 내부에 삽입 및 속도개선되었습니다.
* 기존 비디오 텍스쳐 관련 기능은 2024년까지 지원합니다.
* 새로운 사용법은 [비디오 텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture), [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard)를 참고하시기 바랍니다.

### Improvements to video texture function
* For user convenience, functions after object creation have been inserted into the engine and speed has been improved.
* Existing video texture-related features will be supported until 2024.
* New usage methods include [Video Texture](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture), [Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video), [led board](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard).

## Update

### 2.6.2 (2024/09/05)

#### 1. glTF 모델 회전 오류 수정
* glTF 모델의 회전에 제대로 동작하지 않는 오류를 수정하였습니다.

#### 2. JSObject::setSelectable() 오류 수정
* `JSObject`에서 `setSelectable()`이 제대로 적용되지 않는 오류를 수정하였습니다.

#### 3. 카메라 이동 API 오류 수정
* `JSCamera`에서 `setLocation()`가 제대로 동작하지 않는 오류를 수정하였습니다.

### 2.6.0 (2024/08/30)

#### 1. 지형 쉐이더 컴파일 오류 처리 기능 추가
  * 지형 쉐이더를 컴파일할 경우, 디바이스별로 쉐이더 컴파일 조건이 다르므로 실패하는 경우가 있습니다.
  * 이를 방지하기 위해, 컴파일 실패시 조건 수정후 다시 컴파일하는 기능이 추가되었습니다.
#### 2. 멀티뷰(화면 분할) 모드 오류 수정
  * `멀티뷰 모드`에서 지형이 깜박이던 현상을 수정했습니다.
#### 3. 멀티뷰(화면 분할) 모드 레이어 가시화 기능 추가
  * `멀티뷰 모드`에서, `RTT/하이브리드` 레이어의 가시화를 제어할 수 있는 기능이 추가되었습니다.
#### 4. POI 가시화 개선
  * POI 레벨 범위(시작, 끝)에 따른 가시화 구조를 수정하였습니다.
  * `ETLT_USER_LAYER`를 통해 생성한 POI에 대한 `object_ahead` 옵션 설정에 따른 가시화 기능을 수정하였습니다.
#### 5. Base Map 기능에서, Bing Map(전체)/OSM(Terrain) 항목 서비스 종료
  * Base Map에서, Bing Map과 Open Street Map(terrain)에 대한 서비스를 종료하였습니다.
  * 자세한 사항은 [링크](https://sandbox.egiscloud.com/code/main.do?id=layer_basemap)를 참고해주시기 바랍니다.

### 2.6.2 (2024/09/05)

#### 1. Fixed glTF Model Rotation Issue
* Fixed an issue where the rotation of glTF models was not functioning correctly.

#### 2. Fixed JSObject::setSelectable() Issue
* Fixed an issue where `setSelectable()` in `JSObject` was not applied properly.

#### 3. Fixed Camera Movement API Issue
* Fixed an issue where `setLocation()` in `JSCamera` was not functioning correctly.

### 2.6.0 (2024/08/30)

#### 1. Added Terrain Shader Compilation Error Handling
  * When compiling terrain shaders, the compilation conditions vary by device, which can lead to failures.
  * To prevent this, a feature has been added to modify the conditions and recompile in case of failure.
#### 2. Fixed Multi-View (Split Screen) Mode Error
  * Fixed an issue where the terrain would flicker in `Multi-View Mode`.
#### 3. Added Layer Visibility Control in Multi-View (Split Screen) Mode
  * A feature has been added to control the visibility of `RTT/Hybrid` layers in `Multi-View Mode`.
#### 4. Improved POI Visualization
  * The visualization structure has been adjusted based on the POI level range (start, end).
  * The visualization feature has been modified according to the `object_ahead` option setting for POIs created through `ETLT_USER_LAYER`.
#### 5. Discontinued Bing Map(All)/OSM(Terrain) Services in Base Map
  * The services for Bing Map and Open Street Map (terrain) in the Base Map have been discontinued.
  * For more details, please refer to this [link](https://sandbox.egiscloud.com/code/main.do?id=layer_basemap).

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
