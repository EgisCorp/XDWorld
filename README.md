[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation
  * [Korean] https://egiscorp.gitbook.io/xdworld-webgl-manual
  * [English] https://egiscorp.gitbook.io/xdworld_global_manual
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

### 2.2.2 (2024/5/3)

#### 1. WMS 오류 해결
  * WMS 기능을 사용할 때, 깜박거리는 현상이 수정되었습니다.

### 1.61.0 (2024/4/26)

#### 1. 수인한도분석 상세분석 옵션 추가
  * '수인한도분석' 기능에서, 상세한 분석을 위한 `isdetail` 프로퍼티가 추가되었습니다.
    * true: 그리드 영역에 햇빛이 들지 않는 영역이 있을 경우, 일조량 계산하지 않음.
    * false:절반이상 햇빛이 들면 일조량 계산.

#### 2. HeatMap API에 가중치 매개변수 추가
  - 기존 히트맵 정보를 입력하는 API의 매개변수에 `가중치`가 추가되었습니다.
  - addHeatMapEX(JSVector3D(경도, 위도, 가중치)) : JSMap 클래스
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // 히트맵 설정
      for(var i=0; i<4000; ++i)
      {
          pMap.addHeatMapEX(new Module.JSVector3D(124.0+Math.random()*8.0, 34.0+Math.random()*6.0, 1.0));
      }
    ```
  - addHeatMapsEX(JSVec3Array(경도, 위도, 가중치)) : JSMap 클래스
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // 히트맵 설정
      var vList = new Module.JSVec3Array();
        
      vList.push(new Module.JSVector3D(128.388791, 36.398409, 1.0));
      vList.push(new Module.JSVector3D(126.745337, 35.019302, 2.0));
      vList.push(new Module.JSVector3D(128.902455, 35.319581, 3.0));
      vList.push(new Module.JSVector3D(129.147955, 36.119326, 4.0));
      vList.push(new Module.JSVector3D(129.073899, 37.210022, 5.0));
      vList.push(new Module.JSVector3D(128.373239, 37.765977, 6.0));
      vList.push(new Module.JSVector3D(127.108525, 37.658713, 7.0));
      vList.push(new Module.JSVector3D(126.256902, 36.562545, 8.0));
      vList.push(new Module.JSVector3D(127.445746, 36.108470, 9.0));
      vList.push(new Module.JSVector3D(127.820355, 36.789230, 10.0));
      vList.push(new Module.JSVector3D(127.033226, 37.521304, 1.0));
      vList.push(new Module.JSVector3D(127.042107, 37.520151, 1.0));
      vList.push(new Module.JSVector3D(127.044620, 37.514160, 1.0));
      vList.push(new Module.JSVector3D(127.048812, 37.518277, 1.0));
      vList.push(new Module.JSVector3D(127.030439, 37.506783, 1.0));
      vList.push(new Module.JSVector3D(127.028751, 37.505695, 1.0));

      pMap.addHeatMapsEX(vList);
      pMap.setEffectDistance(2000000);
    ```

### 2.2.2 (2024/5/3)

1. Resolve WMS Error
  * Fix blinking issue when using WMS functionality.

### 1.61.0 (2024/4/26)

#### 1. Detailed Analysis Option Added to Solar Limit Analysis
  * In 'solar limit analysis' feature, a isdetail property has been added for more detailed analysis.
    * true: Do not calculate insolation if there is an area in the grid where sunlight does not reach.
    * false: Calculate insolation if more than half of the area receives sunlight.

#### 2. Weight Parameter Added to HeatMap API
  - `weight` parameter has been added to the parameters of the API for inputting existing heatmap information.
  - addHeatMapEX(JSVector3D(longitude, latitude, weight)) : JSMap class
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // Set HeatMap
      for(var i=0; i<4000; ++i)
      {
          pMap.addHeatMapEX(new Module.JSVector3D(124.0+Math.random()*8.0, 34.0+Math.random()*6.0, 1.0));
      }
    ```
  - addHeatMapsEX(JSVec3Array(longitude, latitude, weight)) : JSMap class
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // Set HeatMap
      var vList = new Module.JSVec3Array();
        
      vList.push(new Module.JSVector3D(128.388791, 36.398409, 1.0));
      vList.push(new Module.JSVector3D(126.745337, 35.019302, 2.0));
      vList.push(new Module.JSVector3D(128.902455, 35.319581, 3.0));
      vList.push(new Module.JSVector3D(129.147955, 36.119326, 4.0));
      vList.push(new Module.JSVector3D(129.073899, 37.210022, 5.0));
      vList.push(new Module.JSVector3D(128.373239, 37.765977, 6.0));
      vList.push(new Module.JSVector3D(127.108525, 37.658713, 7.0));
      vList.push(new Module.JSVector3D(126.256902, 36.562545, 8.0));
      vList.push(new Module.JSVector3D(127.445746, 36.108470, 9.0));
      vList.push(new Module.JSVector3D(127.820355, 36.789230, 10.0));
      vList.push(new Module.JSVector3D(127.033226, 37.521304, 1.0));
      vList.push(new Module.JSVector3D(127.042107, 37.520151, 1.0));
      vList.push(new Module.JSVector3D(127.044620, 37.514160, 1.0));
      vList.push(new Module.JSVector3D(127.048812, 37.518277, 1.0));
      vList.push(new Module.JSVector3D(127.030439, 37.506783, 1.0));
      vList.push(new Module.JSVector3D(127.028751, 37.505695, 1.0));

      pMap.addHeatMapsEX(vList);
      pMap.setEffectDistance(2000000);
    ```

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
