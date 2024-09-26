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

### 2.7.0 (2024/09/27)

#### 1. Off-screen indicator 위치 반환 API 추가
  * 특정 좌표(경도, 위도, 고도)가 화면에 보이지 않는 경우 화면 엣지의 indicator 좌표를 반환하는 API가 추가되었습니다.
  * object getScreenEdgeIndicator(JSVector3D position)
    * JSMath로 호출합니다.
    * 파라미터 정보
        * position(JSVector3D) : Indicator를 반환하고자 하는 경위도, 고도 좌표
    * 반환 정보
        * 해당 지점이 시야 내에 있는 경우 : null 반환
        * 해당 지점이 시야를 벗어나는 경우 : Indicator 위치를 나타내는 화면 가장자리 좌표(속성 x, y 로 구성된 오브젝트)
    * 활용
        ``` javascript
        var position = layer.keyAtObject("TEST_OBJECT").getPosition();
        var indicator = Module.getMath().getScreenEdgeIndicator(position);
        ```

#### 2. 화면분할 기능에서 POI 오류 수정
  * 화면분할 기능에서 커스텀타일 레이어 기반으로 POI를 사용시 정상적으로 표현되지 않는 문제를 수정하였습니다.

#### 3. 엔진 및 웹 워커 JPG 변환 관련 기능 수정(웹 워커 변경 필수)
  * 엔진 및 웹 워커 환경에서, JPG 포맷 이미지의 확인 방법이 변경되었습니다.

#### 4. 바람길 데이터 기능에서 gzip 포맷 압축 기능 추가
  * `JSFlow.createFlow()`의 `url` 파라미터로 `gzip` 포맷도 사용 가능하도록 기능이 추가되었습니다.
    * 이제부터 기존 데이터가 있을 경우, `gzip`으로 압축해서 바로 사용할 수 있습니다.

#### 5. 수인한도분석 선택 기능 오류 수정
  * 수인한도분석 기능에서, 배척격자 선택시 선택이 제대로 되지 않는 오류를 수정하였습니다.

#### 주의 사항
  * 현재 [Viewshed(3D)](https://sandbox.egiscloud.com/code/main.do?id=analysis_viewshed_3d)에서 가시권을 나타내는 폴리곤이 제 위치에 출력되지 않는 오류가 있습니다. 사용에 주의 부탁드리며, 빠른 시일 내로 수정하겠습니다.

### 2.7.0 (2024/09/27)

#### 1. Addition of Off-screen Indicator Position API
  * A new API has been added that returns the coordinates of the indicator at the edge of the screen when a specific point (longitude, latitude, altitude) is off-screen.
  * object getScreenEdgeIndicator(JSVector3D position)
    * You can call through `JSMath`
    * Parameter
        * position(`JSVector3D`) : The longitude, latitude, and altitude coordinates for which you want to return the indicator.
    * Return
        * If the point is within the visible area: returns null
        * If the point is outside the visible area: returns the screen edge coordinates (an object with properties x and y representing the indicator's location).
    * 활용
        ``` javascript
        var position = layer.keyAtObject("TEST_OBJECT").getPosition();
        var indicator = Module.getMath().getScreenEdgeIndicator(position);
        ```

#### 2. Fixed POI Error in Split-screen Feature
  * Fixed an issue where POIs based on custom tile layers were not displayed correctly in the split-screen feature.

#### 3. Changes in JPG Conversion Features for Engine and Web Worker (Web Worker Update Required)
  * The method for verifying JPG format images in the engine and web worker environments has been changed.

#### 4. Added gzip Compression Support for Wind Path Data Feature
  * The url parameter of `JSFlow.createFlow()` now supports `gzip` format
    * Existing data can now be compressed into `gzip` format for direct use.
#### 5. Fixed Error in Maximum Acceptance Limit Analysis Selection
  * Fixed an issue where grid selection was not working properly in the maximum acceptance limit analysis feature.

#### Notice
  * There is currently an issue in [Viewshed(3D)](https://sandbox.egiscloud.com/code/main.do?id=analysis_viewshed_3d) where the polygon representing the viewshed is not displayed in the correct position. We will address this as soon as possible.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
