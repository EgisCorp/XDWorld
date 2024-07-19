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

### 2.4.2 (2024/7/19)

#### 1. 고스트심볼 화면 기반 크기 고정 기능 추가
  * 고스트심볼 렌더링 시 화면의 픽셀을 기준으로 크기를 고정할 수 있는 기능이 추가되었습니다.
  * 크기 고정 시 카메라와의 거리와 상관없이 고스트심볼의 크기가 항상 일정하게 유지됩니다.
  * 크기를 설정하는 경우 JSGhostSymbol의 setScreenFixedSize API를 통해 값을 설정합니다. 
    ``` javascript
    ghostsymbolObject.setScreenFixedSize(50);
    ```
  * 크기를 해제하는 경우 JSGhostSymbol의 setScreenFixedSize API에 null을 설정하면 크기 고정 설정이 해제됩니다.
    ``` javascript
    ghostsymbolObject.setScreenFixedSize(null);
    ```
  * 크기는 3D 공간의 [x:1.0, y:1.0, z:1.0] 공간 당 1픽셀로 치환됩니다.

#### 2. 고스트심볼 맵 모델 삭제 및 참조 오브젝트 수 조회 기능 추가
  * 고스트심볼 맵에 등록한 모델을 등록한 ID 기반으로 삭제하는 API가 추가되었습니다.
    ``` javascript
    var result = Module.getGhostSymbolMap().removeModel("sphere");
    ```
  * 모델을 참조하는 고스트심볼 오브젝트가 있는 경우 삭제되지 않고 false를 반환합니다.
  * 성공적으로 삭제 되었을 경우 true를 반환합니다.
  * 모델을 참조하는 오브젝트의 수는 JSGhostSymbolMap 클래스의 getReferenceCount API로 확인 가능합니다.
    ``` javascript
    var referenceCount = Module.getGhostSymbolMap().getReferenceCount("sphere"));
    ```

#### 3. 레이어 상에서 화면 좌표 기반 영역에 포함되는 오브젝트 키 반환
  * JSLayer에 소속된 오브젝트 중 화면 좌표 기반 사각 영역에 포함되는 오브젝트 목록을 반환하는 API가 추가되었습니다.
    ``` javascript
    var objectKeyList = layer.getObjectInScreenRect(386, 445, 674, 668);
    ```
  * JSPolygon, JSPoint, JSGhostSymbol, JSReal3D 오브젝트 타입 레이어에서 사용 가능합니다. (이 외 오브젝트 타입은 추후 업로드 예정입니다.)

### 2.4.2 (2024/7/19)

#### 1. Addition of Screen-Based Size Fixing Feature for Ghost Symbols
  * A feature has been added that allows the size of Ghost Symbols to be fixed based on the screen's pixels when rendering Ghost Symbols.
  * When the size is fixed, the Ghost Symbol's size remains constant regardless of the distance from the camera.
  * To set the size, use the setScreenFixedSize API of JSGhostSymbol as shown below:
    ``` javascript
    ghostsymbolObject.setScreenFixedSize(50);
    ```
  * To disable the fixed size, set null to the setScreenFixedSize API of JSGhostSymbol to release the fixed size setting.
    ``` javascript
    ghostsymbolObject.setScreenFixedSize(null);
    ```
  * The size is replaced as 1 pixel per [x:1.0, y:1.0, z:1.0] space in the 3D space.

#### 2. Addition of Functions to Delete Map Models and Check Reference Object Count for Ghost Symbols
  * An API has been added to delete models registered in the Ghost Symbol map based on the registered ID.
    ``` javascript
    var result = Module.getGhostSymbolMap().removeModel("sphere");
    ```
  * If there are Ghost Symbol objects referencing the model, it will not be deleted and false will be returned.
  * If successfully deleted, true will be returned.
  * The number of objects referencing the model can be checked using the getReferenceCount API of the JSGhostSymbolMap class.
    ``` javascript
    var referenceCount = Module.getGhostSymbolMap().getReferenceCount("sphere");
    ```

#### 3. Return of Object Keys Included in Screen-Coordinate Based Area on Layer
  * An API has been added to return the list of objects included in the rectangular area based on screen coordinates among the objects belonging to JSLayer.
    ``` javascript
    var objectKeyList = layer.getObjectInScreenRect(386, 445, 674, 668);
    ```
  * This can be used in layers with object types such as JSPolygon, JSPoint, JSGhostSymbol, and JSReal3D. (Other object types will be updated in the future.)

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
