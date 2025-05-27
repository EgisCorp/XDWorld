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

$\huge{\rm{\color{red}Important\ note}}$

$\rm{\color{red}●\ 1인칭\ 카메라\ 비디오\ 텍스쳐\ 기능\ 지원\ 중단}$
  * 기존 1인칭 카메라 비디오 텍스쳐 기능은 2025년까지 지원합니다. 
  * JSCamera 클래스의 삭제 API ---------> JSVideoObject 클래스의 대체 API 
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera 클래스의 삭제 property ---------> JSVideoObject 클래스의 대체 property</summary>
     
     - [x] videoStreaming ---------------> videoStreaming
     - [x] videoFar -----------------------> far
     - [x] videoFovX ---------------------> fovX
     - [x] videoFovY ---------------------> fovY
     - [x] videoAlpha --------------------> alpha
     - [x] videoAxisX --------------------> axisX
     - [x] videoAxisY --------------------> axisY
     - [x] videoZoom --------------------> zoom
     - [x] videoFarPlane -----------------> background
     - [x] videoResolution ---------------> resolution
     - [x] videoObjectMapping ---------> objectMapping
     - [x] videoIsplayer ------------------> isPlayer
   </details>

  * 비디오 객체  [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

$\rm{\color{red}●\ Discontinuation\ of\ First-Person\ Camera\ Video\ Texture\ Feature}$
  * The existing First-Person Camera Video Texture feature will be supported until 2025.
  * JSCamera class removal API ---------> Replacement API in JSVideoObject class
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera class removal properties ---------> Replacement properties in JSVideoObject class</summary>
     
     - [x] videoStreaming ---------------> videoStreaming
     - [x] videoFar -----------------------> far
     - [x] videoFovX ---------------------> fovX
     - [x] videoFovY ---------------------> fovY
     - [x] videoAlpha --------------------> alpha
     - [x] videoAxisX --------------------> axisX
     - [x] videoAxisY --------------------> axisY
     - [x] videoZoom --------------------> zoom
     - [x] videoFarPlane -----------------> background
     - [x] videoResolution ---------------> resolution
     - [x] videoObjectMapping ---------> objectMapping
     - [x] videoIsplayer ------------------> isPlayer
   </details>

  * Please refer to [Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video), [LED Board](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), and [RTT Video](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture).

## Update

- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.

### 2.14.2 (2025/05/27)

#### 1. 고스트심볼에 조망보기, 가시권분석3D 개선
  * 고스트심볼에서 조망보기, 가시권분석(3D) 성능을 향상하였습니다.

#### 2. 카메라 이동 오류 수정 ([issue #495](https://github.com/EgisCorp/XDWorld/issues/495))
  * 같은 위치로 이동할 경우 오류가 발생하여 예외처리를 추가하였습니다.

#### 3. 객체가 지형 밑인지 위인지 사용자가 설정하는 함수
  * 객체가 지형 위, 아래인지에 따라서 투명값 렌더링 순서에 영향이 있어 애매한 객체는 사용자가 직접 지정 가능합니다.(ex : 지하도)
  * JSPolygon::setUnderground(boolean _bUnderground) : 지형 위 아래 설정
  * JSPolygon::getUnderground() : 지정 상태 반환
   ```javascript
        var LayerList = new Module.JSLayerList(true);
        var layer = LayerList.nameAtLayer("Layer");
        if(layer!=null)
        {
                var pObject = layer.keyAtObject("Object");
                if(pObject==null) return;
                       pObject.setUnderground(true);
        }
   ```

#### 4. 거리측정 기능 개선
  * 거리 측정 시 라인 지형결합 on/off 설정 API 추가하였습니다.
     * void setMeasureDistancePointUnionTerrain(bool _set);
       * 이후에 입력되는 라인의 지형결합 적용 여부를 설정할 수 있습니다.
       * Class : JSOption
       * Parameter
         * _set : 지형결합 적용 여부(true/false)
       * 예시
          ``` javascript
          Module.getOption().setMeasureDistancePointUnionTerrain(false);
          ```

#### 5. POI에 가까이 다가가는 경우 사라지는 현상 개선
  * JSLayer의 minDistance 값보다 큰 거리에서 POI가 사라지는 현상을 수정하였습니다.


### 2.14.1 (2025/05/19)

#### 1. JSLayer에 setAlpha API의 동작 방식 변경
  * 기존 Object의 속성을 일괄적 조회후 수정 방식에서 실시간 적용 방식으로 변경
  * 슬라이드 방식으로 투명도 처리 가능

#### 2. JSEditTerrain 개별 삭제 기능 추가 ([issue #492](https://github.com/EgisCorp/XDWorld/issues/492))
  * 성절토 List index로 삭제할 수 있는 기능 추가

#### 3. 좌표변환 추가 ([issue #494](https://github.com/EgisCorp/XDWorld/issues/494))
  * 기존 WMS의 지원 좌표계는 5개(4326, 5174, 5179, 5180, 5186)
  * EPSG:3765 좌표변환 추가
  * 다른 EPSG 좌표계 지원할 수 있도록 추가

#### 4. moveLonLatBoundarybyJson API 오류 수정 ([issue #495](https://github.com/EgisCorp/XDWorld/issues/495))
  * 이동 후 똑같은 위치로 다시 이동시 오류 발생하여 예외처리

#### 5. 이미지 오버레이 기능 오류 수정 ([issue #496](https://github.com/EgisCorp/XDWorld/issues/496))
  * 이미지 오버레이시 지형 결합되지 않는 오류 수정


### 2.14.0 (2025/05/12)

#### 1. JSCamera의 moveOvalDist 이동 기준 해제 ([issue #488](https://github.com/EgisCorp/XDWorld/issues/488))
  * API 실행 시 이동 여부 기준 100m를 해제하였습니다.
#### 2. 경사향 가시화 결과 갱신 오류 수정 ([issue #488](https://github.com/EgisCorp/XDWorld/issues/490))
  * 경사향 가시화 결과가 갱신되지 않는 현상을 수정하였습니다.
#### 3. 태풍 위험반경 표시 오류 수정
  * RTT 기반 태풍 위험반경이 표시되지 않는 현상을 수정하였습니다.
#### 4. JSHTMLObject 스테레오뷰 오류 수정 ([issue #491](https://github.com/EgisCorp/XDWorld/issues/491))
  * JSHTMLObject 스테레오뷰 실행시 위치 오류를 수정하였습니다.


### 2.14.2 (2025/05/27)

#### 1. Improved visibility and visibility analysis 3D in Ghost Symbol
  * Improved performance of viewing and visibility analysis (3D) in Ghost Symbol.

#### 2. Fixed camera movement error ([issue #495](https://github.com/EgisCorp/XDWorld/issues/495))
  * An exception handling was added to prevent an error from occurring when moving to the same location.

#### 3. A function that allows the user to set whether an object is under or over the terrain
  * Since the order of rendering transparency values ​​is affected depending on whether the object is above or below the terrain, users can directly specify ambiguous objects (ex: underpasses).
  * JSPolygon::setUnderground(boolean _bUnderground) : Terrain top and bottom settings
  * JSPolygon::getUnderground() : Returns specified status
   ```javascript
        var LayerList = new Module.JSLayerList(true);
        var layer = LayerList.nameAtLayer("Layer");
        if(layer!=null)
        {
                var pObject = layer.keyAtObject("Object");
                if(pObject==null) return;
                       pObject.setUnderground(true);
        }
   ```

#### 4. Improved distance measurement function
  * Added API to turn on/off line terrain combination when measuring distance
     * void setMeasureDistancePointUnionTerrain(bool _set);
       * You can set whether to apply terrain combination to lines entered later.
       * Class : JSOption
       * Parameter
         * _set : Whether to apply terrain combination(true/false)
       * 예시
          ``` javascript
          Module.getOption().setMeasureDistancePointUnionTerrain(false);
          ```

#### 5. Improved the phenomenon of disappearing when approaching a POI
  * Fixed an issue where POIs would disappear at distances greater than JSLayer's minDistance value.


### 2.14.1 (2025/05/19)

#### 1. Changed the behavior of the setAlpha API in JSLayer
  * Changed the method of batch-reviewing and then modifying the properties of existing objects to real-time application
  * Transparency can be processed in slide mode

#### 2. Added individual delete function to JSEditTerrain ([issue #492](https://github.com/EgisCorp/XDWorld/issues/492))
  * Added the ability to delete by cutting and fill List index

#### 3. Add coordinate conversion ([issue #494](https://github.com/EgisCorp/XDWorld/issues/494))
  * The existing WMS supports 5 coordinate systems (4326, 5174, 5179, 5180, 5186)
  * Added EPSG:3765 coordinate transformation
  * Added support for other EPSG coordinate systems

#### 4. moveLonLatBoundarybyJson API error correction ([issue #495](https://github.com/EgisCorp/XDWorld/issues/495))
  * An error occurs when moving to the same location again after moving, so an exception is handled

#### 5. Image overlay function error correction ([issue #496](https://github.com/EgisCorp/XDWorld/issues/496))
  * Fixed terrain not combining when overlaying images


### 2.14.0 (2025/05/12)
#### 1. Removed movement threshold in JSCamera.moveOvalDist ([issue #488](https://github.com/EgisCorp/XDWorld/issues/488))
  * The 100-meter movement threshold has been removed from the API execution condition.

#### 2. Fixed slope direction visualization update bug ([issue #488](https://github.com/EgisCorp/XDWorld/issues/490))
  * Resolved an issue where the slope direction visualization was not updating properly.

#### 3. Fixed typhoon risk radius display issue
  * Resolved an issue where the RTT-based typhoon risk radius was not being displayed.
    
#### 4. Fixed stereo view position error in JSHTMLObject ([issue #491](https://github.com/EgisCorp/XDWorld/issues/491))
  * Fixed a position error that occurred when executing stereo view in JSHTMLObject.



## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
