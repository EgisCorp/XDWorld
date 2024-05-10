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

### beta 2.2.3 (2024/5/10)

#### 1. POI 가시화 오류 수정
  - 높은 고도에서, POI 데이터 지구 반대편 객체가 보이는 오류가 수정되었습니다.

#### 2. 카메라 자동 이동시 폴리곤 오브젝트 깜박임 오류 수정
  - 카메라 자동 이동 모드에서, 지형과 높이가 비슷한 폴리곤이 깜박이는 오류가 수정되었습니다.

#### 3. 타일레이어에 하이브리드, WMS에 대한 최대레벨 이상 지형 렌더링에 상위 데이터를 참조하는 기능 추가
  * 하이브리드 및 WMS에 대한 처리는 지형의 레벨과 동일한 구간만 화면에 오버레이 됩니다.
  * 오버레이 레벨이 13레벨이 최대일때 14를 초과하는 지형레벨 구간에서 오버레이가 사라져서 세부 데이터 구축을 하지 않아도 13레벨의 오버레이 이미지를 활용하여 남은 14이후의 지형에 오버레이를 연장해주는 기능입니다.
  *  `JSLayerList.createXDServerLayer(_option)`에 `_option` 구조에 `maxLevelOverlap : bool` 속성이 추가되었습니다. (선택적, 기본값 : false )
  *  `bool JSLayer::setMaxLevelOverlap(bool _bOverlap)` API 추가되었습니다.
    *   기본적으로 `maxLevelOverlap` 속성과 동일하며, 타일 레이어 구조 and ETLT_PNG_IMAGE, ETLT_WMS가 아니면 false를 반환합니다.

#### 4. 커스텀타일 레이어에서 HTML 객체에 숨김 처리 오류 수정
  - 커스텀타일 레이어에서 EOT_HTML (HTML 객체)에 대한 Culling 숨김 처리 오류가 수정되었습니다.
  *   [이슈#398에 대한 수정]( https://github.com/EgisCorp/XDWorld/issues/398#issue-2274483934)

### beta 2.2.2 (2024/5/3)

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

### beta 2.2.3 (2024/5/10)
#### 1. Correction of POI Visualization Error
  - At high altitudes, the issue of POI data displaying objects on the opposite side of the Earth has been fixed.
#### 2. Fix for Polygon Object Blinking During Camera Auto-Movement
  - In automatic camera movement mode, an issue where polygons with similar terrain and height would blink has been resolved.
#### 3. Addition of Feature to Reference Higher Data for Rendering Terrain Beyond Maximum Level for Hybrid and WMS Layers
  - Processing for hybrid and WMS layers will now overlay only segments of the terrain equivalent to the level of the terrain.
  - When the overlay level is at its maximum at level 13, the feature extends overlay to the terrain beyond level 14, utilizing the overlay images of level 13 without needing to construct detailed data for the terrain after level 14.
  - The _option structure in JSLayerList.createXDServerLayer(_option) has added a maxLevelOverlap: bool attribute. (Optional, Default: false)
  - An API bool JSLayer::setMaxLevelOverlap(bool _bOverlap) has been added.
    - By default, it returns false if the layer structure is not a tile layer and ETLT_PNG_IMAGE, ETLT_WMS.
#### 4. Correction of Hidden Treatment Error for HTML Objects in Custom Tile Layers
  - An error in culling hidden treatment for EOT_HTML (HTML objects) in custom tile layers has been fixed.
  *   [이슈#398에 대한 수정]( https://github.com/EgisCorp/XDWorld/issues/398#issue-2274483934)

### beta 2.2.2 (2024/5/3)

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
