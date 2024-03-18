[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual
### Demos & Sandbox - https://sandbox.egiscloud.com
### Demos & Sandbox (beta) : https://sandbox.egiscloud.com/code/main.do?id=start&engine=beta&worker=true

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

### 1.59.2 / beta 2.1.2 (2024/3/15)

#### 1.  ETLT_TILE_LOD_MODEL 레이어 삭제시 오류 수정
  * 레이어 삭제 요청시, 해당 핸들이 남아있어 발생하는 오류를 수정하였습니다.
#### 2. 그림자 색상 변경 API 수정
  * JSAnalysis::setShadowColor() API의 색상 설정이 적용되지 않는 오류를 수정하였습니다.
#### 3.  https://github.com/EgisCorp/XDWorld/issues/391 이슈 수정
  * 선 두께가 1일때 점선이 그려지지 않은 현상을 수정하였습니다.

### 1.59.1 / beta 2.1.1 (2024/3/8)

#### 1. createShadow API 실행 시 마우스 모드 고정 현상 수정 
  * JSAnlysis의 createShadow API 실행 시 마우스 모드가 일반 모드(1번)으로 고정되는 현상을 수정하였습니다. 

#### 2. JSFlowPolygon의 setHeight API 설정 오류 수정
  * setHeight API 설정 값에 오차가 발생하는 현상을 수정하였습니다.

#### 3. ETLT_TILE_LOD_MODEL 레이어의 LOD Max값 관련 함수 추가
  * JSLayer 클래스에 ETLT_TILE_LOD_MODEL 타입 레이어의 LOD Max 값을 설정/반환 하는 API가 추가되었습니다.
  * setTileLODMaxLevel(_nMaxLevel) : LOAD Max 값을 설정합니다(`-1`일 경우, 제한 없음). 기본값은 `-1`입니다.
  * getTileLODMaxLevel() : LOAD Max 값을 반환합니다.
    ``` javascript
    var layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("bldg_us_jsp");
    layer.setTileLODMaxLevel(3);
    ```
### 1.59.0 / beta 2.1.0 (2024/2/23)
#### 1. 초기 로딩시 지구본이 검게 표현되는 현상 수정
- 엔진 로드 직후 지형 이미지가 완전 수신 되지 않아 지구본이 검은색으로 표현 되는 현상을 수정하였습니다.

#### 2. 서버 기반 지형 고도 반환 함수 추가
- 현재 엔진에서 요청 중인 지형 서버로 DEM 고도 값을 수신하는 API가 추가되었습니다.

- 서버의 고도 값을 리턴하므로 엔진에 낮은 레벨 지형이 로드 된 상태인 경우, 현재 엔진 지형과 DEM 값이 다를 수 있습니다.

- 값은 비동기로 반환되므로 콜백 함수를 통해 값을 수신합니다.

- 입력한 경위도 및 지형 레벨에 대응되는 고도 값이 없거나 서버에 지형 데이터가 없는 경우 null을 반환합니다.

``` javascript
Module.getTerrain().getServerAltitude({
    level : 15,
    positions : [
        new Module.JSVector2D(127.055035334602, 37.48664424515323),
        new Module.JSVector2D(127.05509237777562, 37.48664424515323),
        new Module.JSVector2D(127.05509237777562, 37.48668970070035)
    ]
}, function (result) {
    console.log(result);
})

// 반환 값
(3) [{…}, {…}, {…}]
> 0 : {longitude: 127.055035334602, latitude: 37.48664424515323, altitude: 9.70352554321289}
> 1 : {longitude: 127.05509237777562, latitude: 37.48664424515323, altitude: 9.70939826965332}
> 2 : {longitude: 127.05509237777562, latitude: 37.48668970070035, altitude: null}    // 고도 값이 없는 경우 null 반환
   length : 3
```
#### 3. 점선 라인 생성 오류 추가
* JSLineString 객체의 점선 속성이 적용되지 않는 현상을 수정하였습니다.

<br>

### 1.59.2 / beta 2.1.2 (2024/3/15)

#### 1. Fix error when deleting ETLT_TILE_LOD_MODEL layer
  * Fixed an error occurring due to lingering handles when deleting the layer.
#### 2. API modification for changing shadow color
  * Resolved an issue where the color setting of the JSAnalysis::setShadowColor() API was not being applied.
#### 3. Issue resolution for https://github.com/EgisCorp/XDWorld/issues/391
  * Corrected the phenomenon where dashed lines were not drawn when the line thickness was 1.

### 1.59.1 / beta 2.1.1 (2024/3/8)

#### 1. Fixed an issue where mouse mode was locked when executing the createShadow API
  * Fixed an issue where the mouse mode was locked to normal mode (1) when executing the JSAnalysis's createShadow API.

#### 2. Fixed a setting error in JSFlowPolygon's setHeight API
  * Corrected an issue where there was a discrepancy in the setHeight API setting value.

#### 3. Added functions related to the LOD Max value of the ETLT_TILE_LOD_MODEL layer
  * Added APIs in the JSLayer class to set/return the LOD Max value for the ETLT_TILE_LOD_MODEL type layer.
  * setTileLODMaxLevel(_nMaxLevel): Sets the LOD Max value (-1 for no limit). The default is -1.
  * getTileLODMaxLevel(): Returns the LOD Max value.
    ``` javascript
    var layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("bldg_us_jsp");
    layer.setTileLODMaxLevel(3);
    ```
### 1.59.0 / beta 2.1.0 (2024/2/23)
#### 1. Fixed an issue where the globe appeared black during initial loading
- Corrected an issue where the globe appeared black immediately after engine load due to incomplete reception of terrain images.

#### 2. Added a function to return terrain elevation from the server
- Added an API to receive DEM elevation values from the terrain server currently being requested by the engine.
- Since it returns the elevation value from the server, the current engine terrain and DEM values may differ if low-level terrain is loaded in the engine.
- The value is returned asynchronously, so it is received through a callback function.
- If there is no elevation value corresponding to the input latitude, longitude, and terrain level, or if there is no terrain data on the server, null is returned.

``` javascript
Module.getTerrain().getServerAltitude({
    level : 15,
    positions : [
        new Module.JSVector2D(127.055035334602, 37.48664424515323),
        new Module.JSVector2D(127.05509237777562, 37.48664424515323),
        new Module.JSVector2D(127.05509237777562, 37.48668970070035)
    ]
}, function (result) {
    console.log(result);
})

// Return value
(3) [{…}, {…}, {…}]
> 0 : {longitude: 127.055035334602, latitude: 37.48664424515323, altitude: 9.70352554321289}
> 1 : {longitude: 127.05509237777562, latitude: 37.48664424515323, altitude: 9.70939826965332}
> 2 : {longitude: 127.05509237777562, latitude: 37.48668970070035, altitude: null}    // 고도 값이 없는 경우 null 반환
   length : 3
```
#### 3. Fixed an issue with creating dashed lines
* Corrected a problem where the dashed line attribute of the JSLineString object was not being applied.


## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
