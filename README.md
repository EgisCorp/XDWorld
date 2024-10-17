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

### 2.7.2 (2024/10/17)

#### 1. 가시권 분석(3D) 오류 수정
  * 가시권 분석 기능에서, 가시권 폴리곤의 위치가 제대로 갱신되지 않는 오류를 수정하였습니다.

#### 2. JSAnalysis::checkInsideArea() 기능 확장
  * JSAnalysis::checkInsideArea() API가 분리된 여러 개의 영역에서도 폴리곤의 인접 여부를 확인할 수 있도록 수정하였습니다.
  * 자세한 사용법은 빠른 시일 내로 문서에 업로드할 예정입니다.

#### 3. glTF 애니메이션 기능 추가
  * glTF 포맷의 애니메이션 데이터를 처리할 수 있도록 기능이 확장되었습니다.

#### 4. JSPolygon::renderSelectObject 오류 수정
  * JSPolygon에서 양면을 생성했을 때 뒷면이 보이지 않는 오류를 수정하였습니다.

#### 5. 비디오 객체 오류 수정
  * 비디오 객체에서, 특정 색상 편집 및 투명값일 경우 지형을 무시하는 현상을 수정하였습니다.

### 2.7.1 (2024/10/02)

#### 모바일 환경 측정 및 객체 선택 기능 추가
  * 모바일 환경에서도 거리/면적/고도 측정 및 객체 선택이 가능하도록, 터치 이벤트 처리 기능을 추가하였습니다.
  * 이에 따라 지원하는 모드는 아래와 같습니다
    * `MML_ANALYS_DISTANCE_STRAIGHT`, `MML_ANALYS_AREA_PLANE`, `Module.MML_ANALYS_ALTITUDE`, `MML_SELECT_POINT`
  * `MML_ANALYS_DISTANCE_STRAIGHT`(거리 측정) 모드의 경우, 모바일 환경은 더블 클릭이 불가능하므로, `같은 위치를 1초 이상 터치할시`거리 측정 리스트를 생성하도록 인터페이스를 변경하였습니다.
  * 이후 편리한 사용을 위한 인터페이스 개선이 진행될 예정입니다.

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


### 2.7.2 (2024/10/17)

#### 1. Fixed visibility analysis(3D) error
  * Fixed an issue where the visibility polygon's position was not properly updated in viewshed3D.

#### 2. Expanded JSAnalysis::checkInsideArea() function
  * The JSAnalysis::checkInsideArea() API has been updated to check the adjacency of polygons even across multiple separated areas.
  * Detailed usage will be uploaded to the documentation shortly.

#### 3. Added glTF animation functionality
  * Extended functionality to process animation data in the glTF format.

#### 4. Fixed JSPolygon::renderSelectObject error
  * Fixed an issue where the backside was not visible when generating double-sided polygons in JSPolygon.

#### 5. Fixed video object error
  * Fixed an issue where the terrain was ignored when editing specific colors or transparency values in video objects.

### 2.7.1 (2024/10/02)

#### Added Measurement and Object Selection Features for Mobile Environments
  * Added touch event handling to enable distance, area, altitude measurement, and object selection in mobile environments.
  * Supported modes are as follows:
    * `MML_ANALYS_DISTANCE_STRAIGHT`, `MML_ANALYS_AREA_PLANE`, `Module.MML_ANALYS_ALTITUDE`, `MML_SELECT_POINT`
  * In `MML_ANALYS_DISTANCE_STRAIGHT (distance measurement)` mode, since double-clicking is not possible in mobile environments, the interface has been changed so that a distance measurement list is generated when the user touches the same location for more than 1 second.
  * Interface improvements for easier use are planned for future updates.

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
