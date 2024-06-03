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

### 2.3.1 (2024/5/31)

#### 1. (중요)glTF 최적화(WebWorker)
  - glTF 포맷과 관련하여, WebWorker가 업데이트 되었습니다.
  - 업데이트된 WebWorker 빌드 파일의 사용을 권장합니다.

#### 2. JSColorGrid3D 오브젝트 속성 반환 함수 추가
  * JSColorGrid3D 오브젝트의 속성 반환 함수가 추가되었습니다.
  * [getCellBox] 인덱스에 해당하는 셀의 박스 좌표 정보를 반환합니다.
    * 박스 좌표는 상단/하단, 좌/우, 위/아래로 구분되는 좌표 8개를 반환합니다.
    * 반환 되는 박스의 좌표 속성 값의 순서는 아래와 같습니다.
      * 0 : upLeftTop
      * 1 : upRightTop
      * 2 : upRightBottom
      * 3 : upLeftBottom
      * 4 : downLeftTop
      * 5 : downRightTop
      * 6 : downRightBottom
      * 7 : downLeftBottom
    ``` javascript
    var cellBox = grid.getCellBox(20, 12);
    ```
  * [getCellHeight] 인덱스에 해당하는 셀의 높이 값을 반환합니다.
    ``` javascript
      var height= grid.getCellHeight(20, 12);
    ```
  * [getCellWidthCount] 그리드의 가로 셀 수를 반환합니다.
    ``` javascript
      var widthCellCount= grid.getCellWidthCount();
    ```
  * [getCellHeightCount] 그리드의 세로 셀 수를 반환합니다.
    ``` javascript
      var heightCellCount= grid.getCellHeightCount();
    ```

### 2.3.0 (2024/5/24)

#### 1. JSColorGrid 오브젝트 반환 기능 추가
  * JSLayer의 오브젝트 반환 시 JSColorGrid 오브젝트도 반환 가능하도록 기능을 추가하였습니다.

#### 2. 수인한도분석 진행률 반환 기능 추가
  * CJSAnalysisGridShadow::prograss 분석 진행률을 반환하는 callback 함수를 추가하였습니다.

#### 3. 수인한도분석 배척격자 오류 수정
  * 배척격자가 그림자를 생성하거나, 선택이 되지 않는 오류가 수정되었습니다.

#### 4. JSPolygon으로 고스트 심볼 생성하는 기능 추가
  - 고스트 심볼을 생성할 때 외부에서 모델 파일을 입력해주는 대신, 미리 생성한 JSPolygon으로 정의가 가능하도록 `JSGhostSymbolMap.insert()`에 `polygon`인자를 추가하였습니다.
  - 자세한 사용법은 [샌드박스 - Ghostsymbol(Polygon)](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_to_ghost_symbol)을 참고해주시기 바랍니다.

### 2.3.1 (2024/5/31)

#### 1. (Important) glTF Optimization (WebWorker)
  - The WebWorker related to the glTF format has been updated.
  - It is recommended to use the updated WebWorker build file.

#### 2. Added Property Retrieval Functions for JSColorGrid3D Object
  * Property retrieval functions for the JSColorGrid3D object have been added.
  * [getCellBox] Returns the box coordinates of the cell corresponding to the index.
    * The box coordinates return 8 points corresponding to the top/bottom, left/right, and front/back of the box.
    * The order of the box coordinate properties returned is as follows:
      * 0 : topLeftBack
      * 1 : topRightBack
      * 2 : topRightFront
      * 3 : topLeftFront
      * 4 : bottomLeftBack
      * 5 : bottomRightBack
      * 6 : bottomRightFront
      * 7 : bottomLeftFront
    ``` javascript
    var cellBox = grid.getCellBox(20, 12);
    ```
  * [getCellHeight] Returns the height of the cell corresponding to the index.
    ``` javascript
      var height= grid.getCellHeight(20, 12);
    ```
  * [getCellWidthCount] Returns the number of horizontal cells in the grid.
    ``` javascript
      var widthCellCount= grid.getCellWidthCount();
    ```
  * [getCellHeightCount] Returns the number of vertical cells in the grid.
    ``` javascript
      var heightCellCount= grid.getCellHeightCount();
    ```

### 2.3.0 (2024/5/24)

#### 1. Added Functionality to Return JSColorGrid Object
  - Added functionality to return JSColorGrid object when returning objects from JSLayer.

#### 2. Added Functionality to Return Progress of Analysis Grid Shadow
  - Added callback function CJSAnalysisGridShadow::progress to return the progress of analysis.

#### 3. Fixed Error in Analysis Grid Rejection
  - Fixed an error where the rejection grid would generate shadows or not be selectable.

#### 4. Added Functionality to Generate Ghost Symbols with JSPolygon
  - When generating ghost symbols, added the ability to define them using pre-created JSPolygon instead of inputting a model file from external sources, by adding a polygon argument to JSGhostSymbolMap.insert().
  - For detailed usage, please refer to [Ghostsymbol(Polygon)](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_to_ghost_symbol).

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
