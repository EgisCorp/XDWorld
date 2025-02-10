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

### 2.11.0 (2025/02/10)

1. `3DTiles` 높이 오프셋 옵션 추가
     - `import3DTiles()`에 높이 오프셋(단위 m)를 설정할 수 있는 옵션 `offsetZ`가 추가되었습니다.
     - 자세한 사용법은 아래 예시를 확인해주시기 바랍니다.
       ```javascript
       var pLayerList = new Module.JSLayerList(true);
       if(pLayerList==null) return;

       var pLayer = pLayerList.nameAtLayer("Layer3DTiles");
       if(pLayer==null)
       {
         pLayer = pLayerList.createLayer("Layer3DTiles", Module.ELT_3DTILES);
       }
       pLayer.import3DTiles({
         url : _strURL,
         autoMove : true,
         offsetZ : _fOffsetZ,  // 높이 오프셋. 단위 m
       });
       ```

2. 성절토 바닥/옆면 타일링 텍스쳐 설정 API 추가
     * 성절토 바닥 텍스쳐 설정 시 텍스쳐 반복 출력(타일링)이 가능하도록 API가 추가되었습니다.
     * API 설정 시 1.0보다 큰 값을 n값을 입력하면 설정한 텍스쳐가 n번 반복 출력됩니다.
     * API 호출 이후 생성되는 성절토 객체에 해당 값이 적용됩니다.
     * 성절토 바닥면 텍스쳐 설정
       * bool setBottomTextureTilingScale(float u, float v)
         * class : JSEditTerrain
         * parameter
           * u : 가로 반복 u 좌표
           * v : 세로 반복 v 좌표 
      * 성절토 옆면 텍스쳐 설정
        * bool setSlopeTextureTilingScale(float u, float v)
          * class : JSEditTerrain
          * parameter
            * u : 가로 반복 u 좌표
            * v : 세로 반복 v 좌표 
     ``` javascript
     Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
     Module.getEditTerrain().setSlopeTextureTilingScale(10.0, 10.0);
     ```

3. 비디오 객체 오류 수정
    * 초기화 시 계속적으로 Hls 네트워크 요청하는 오류가 수정되었습니다.
    * 뒷배경 on/off 기능이 추가되었습니다. [비디오 객체](https://sandbox-test.egiscloud.com/code/main.do?engine=latest_test&id=object_video_placement)

4. `JSLayer::setObjectVisibleWithBoundary()` API 추가
   - 매개변수로 전달한 좌표를 벗어날 경우, 오브젝트를 그리지 않도록 설정하는 함수를 추가하였습니다.
   - 함수 정보
     - boolean setObjectVisibleWithBoundary(number minLon, number maxLon, number minLat, number maxLat)
     - class : JSLayer
     - parameter
       - minLon: 최소 경도
       - maxLon: 최대 경도
       - minLat : 최소 위도
       - maxLat : 최대 위도
     ```javascript
      // 레이어 및 오브젝트 생성
      sampleLayer.setObjectVisibleWithBoundary(129.5, 130, 35.16, 35.19);
     ```

### 2.11.0 (2025/02/10)

1. Added `3DTiles` Height Offset Option
     - The `import3DTiles()` function now includes an `offsetZ` option that allows setting a height offset (unit: meters).
     - Please refer to the example below for detailed usage.
       ```javascript
       var pLayerList = new Module.JSLayerList(true);
       if(pLayerList==null) return;

       var pLayer = pLayerList.nameAtLayer("Layer3DTiles");
       if(pLayer==null)
       {
         pLayer = pLayerList.createLayer("Layer3DTiles", Module.ELT_3DTILES);
       }
       pLayer.import3DTiles({
         url : _strURL,
         autoMove : true,
         offsetZ : _fOffsetZ,  // Height offset (unit: meters)
       });
       ```

2. Added API for Tiling Texture Settings on the Bottom/Side of Cut Terrain
     * A new API has been added to allow texture tiling (repeating output) when setting the bottom texture of cut terrain.
     * When setting the API, entering a value greater than 1.0 as n will repeat the assigned texture n times.
     * This value will apply to cut terrain objects created after the API call.
     * Setting the Bottom Texture of Cut Terrain
       * bool setBottomTextureTilingScale(float u, float v)
         * class : JSEditTerrain
         * parameter
           * u : Horizontal tiling (U coordinate)
           * v : Vertical tiling (V coordinate)
      * Setting the Side Texture of Cut Terrain
        * bool setSlopeTextureTilingScale(float u, float v)
          * class : JSEditTerrain
          * parameter
            * u : Horizontal tiling (U coordinate)
            * v : Vertical tiling (V coordinate)
     ``` javascript
     Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
     Module.getEditTerrain().setSlopeTextureTilingScale(10.0, 10.0);
     ```

3. Fixed Video Object Issues
    * Fixed an issue where HLS network requests were continuously made during initialization.
    * Added an on/off feature for the background. [Video Object](https://sandbox-test.egiscloud.com/code/main.do?engine=latest_test&id=object_video_placement)

4. Added `JSLayer::setObjectVisibleWithBoundary()` API
   - Added a function that prevents objects from rendering when they are outside the specified coordinate boundaries.
   - Function Details
     - boolean setObjectVisibleWithBoundary(number minLon, number maxLon, number minLat, number maxLat)
     - class : JSLayer
     - parameter
       - minLon: Minimum longitude
       - maxLon: Maximum longitude
       - minLat : Minimum latitude
       - maxLat : Maximum latitude
     ```javascript
      // Create layer and set object visibility within boundaries
      sampleLayer.setObjectVisibleWithBoundary(129.5, 130, 35.16, 35.19);
     ```

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
