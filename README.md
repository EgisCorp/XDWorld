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

### 2.8.1 (2024/11/01)

#### 1. JSTraceTarget의 glTF 애니메이션 포맷 지원
  * JSTraceTarget에서 애니메이션이 포함된 glTF 포맷을 지원하도록 기능이 확장되었습니다.

#### 2. Real3DPack의 객체 버전 확장 적용
  * Real3DPack 레이어가 다양한 버전의 객체를 사용할 수 있도록 기능이 확장되었습니다.

### 2.8.0 (2024/10/25)

#### 1. 지형과 알파 값이 있는 객체 간의 렌더링 순서 정리
  * 지형과 알파(투명) 값이 존재하는 객체들과의 가시화가 어색하지 않도록, 렌더링 순서를 변경하였습니다.

#### 2. 파이프 색상 변경 오류 수정
  * 간소화 상태에서 파이프 색상 변경 시 색상 값이 정상적으로 적용되지 않는 현상을 수정하였습니다.

#### 3. 외부 폰트 기반 POI Text 이미지 생성시 발생하는 오류 수정
  * Text 이미지 생성이 정상적으로 작동되지 않는 현상을 수정하였습니다.

#### 4. 소형 시설물의 LOD Texture 미적용 오류 수정
  * 카메라 거리에 따른 시설물 LOD 변경 기능이 동작되지 않는 현상을 수정하였습니다.

#### 5. JSPolygon::createVerticalGrid() API 추가
  * 수직 평면 그리드 객체를 생성하는 API가 추가되었습니다.
  * 파라미터: 레이어명, 좌하단, 우상단, 새로 개수, 가로 개수
  * 자세한 사용법은 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_vertical_grid)를 참고해주시기 바랍니다.

#### 6. JSFigure::getRectInfo() API 추가
  * 생성된 `Figure` 객체에서 4개의 꼭지점을 반환합니다.
  * 자세한 사용법은 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_figure_coordinate)를 참고해주시기 바랍니다.


### 2.8.1 (2024/11/01)

#### 1. glTF Animation Format Support in JSTraceTarget
  * JSTraceTarget has been enhanced to support glTF format with animations included.
#### 2. Expanded Object Version Compatibility in Real3DPack
  * The Real3DPack layer has been expanded to accommodate various versions of objects.

### 2.8.0 (2024/10/25)

#### 1. Adjusting Rendering Order between Terrain and Objects with Alpha Values
  * The rendering order has been adjusted to ensure that visualization between terrain and objects with alpha(transparency) values appears natural.

#### 2. Fixing Pipe Color Change Error
  * Fixed an issue where color changes for pipes were not applied correctly in simplified mode.

#### 3. Fixing Error in Generating POI Text Images with External Fonts
  * Resolved an issue where text images were not generated correctly.

#### 4. Fixing LOD Texture Application Error for Small Facilities
  * Fixed an issue where the LOD change function for facilities based on camera distance was not functioning.

#### 5. Adding JSPolygon::createVerticalGrid() API
  * Added an API to create a vertical grid object.
  * Parameters: Layer name, bottom-left corner, top-right corner, number of vertical divisions, number of horizontal divisions.
  * For detailed usage, please refer to [link](https://sandbox.egiscloud.com/code/main.do?id=object_vertical_grid).

#### 6. Adding JSFigure::getRectInfo() API
  * Returns the four vertices of a Figure object.
  * For detailed usage, please refer to [link](https://sandbox.egiscloud.com/code/main.do?id=object_figure_coordinate).


#### Notice
  * There is currently an issue in [Viewshed(3D)](https://sandbox.egiscloud.com/code/main.do?id=analysis_viewshed_3d) where the polygon representing the viewshed is not displayed in the correct position. We will address this as soon as possible.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
