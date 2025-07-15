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

### 2.16.1 (2025/07/15)
#### 1. 고용량 3DS 로딩 최적화 기능이 추가되었습니다.

```javascript
var polygon = Module.createPolygon("POLYGON_3DS_LOAD");
	polygon.loadFile({
		url : _strURL,
		align : "center",
		position : pos,
		rotate :  fAngle,
		rebuild : true,
		discardVertexData : true,   // 추가 : 좌표 GPU 업데이트 후 삭제
		compressObject : false,     // 추가 : Import 후 압축 vertex 압축 안함.
	});
```
#### 2. 건물 높이 기준 횡단면 선분 추출 기능 추가
   * 지정한 건물의 높이기준 외곽선분 추출 기능이 추가되었습니다.
   * object JSReal3D::getFloorSliceEdge(double _height) 
   * 반환값 예시
 ``` {
 {
    "header": {
        // 데이터 바운더리 최소, 최대 경위도
        "minLon": 126.927487351387,    
        "minLat": 37.52418520251252,
        "maxLon": 126.92795509699533,
        "maxLat": 37.52453873807533,
        // 설정한 단면 분석 높이
        "cutHeight": 12.5,
        // 설정한 건물의 중심점
        "location": {
            "lon": 126.92774196141701,
            "lat": 37.52434050186833,
            "alt": 39.250494956970215
        },
        // 건물의 최소, 최대 높이 (해발고도)
        "elevation": {
            "min": 12.125300407409668,
            "max": 66.37568950653076
        }
    },
    // 단면 선분 정보 [A점(경도,위도,높이)B점(경도,위도,높이)] [...] 
    "edge": [
        [
            126.9277111803299,
            37.52448908205179,
            22.275913742370903,
            126.927487351387,
            37.52435413856168,
            22.275933586061
        ],
        [
            126.9277111803299,
            37.52448908206028,
            22.27591446880251,
            126.92779354446381,
            37.524538738067506,
            22.27593025751412
        ],
       [ 
           ...
        ]
    ]
}
```


### 2.16.0 (2025/07/07)
#### 1. Camera 이동 관련 API 오류 수정
  * [카메라 이동](https://sandbox.egiscloud.com/code/main.do?id=camera_set_viewrect)
  * 카메라 이동시 설정된 위치가 아닌 다른 위치로 이동되는 오류가 있어 수정되었습니다.

#### 2. POI ahead 옵션 오류 수정
  * [Object ahead](https://sandbox.egiscloud.com/code/main.do?id=object_ahead)
  * POI ahead 옵션이 동작하지 않아 수정되었습니다.

#### 3. Tile Layer 요청 제한 기능 개선
  * [Request Limit](https://sandbox.egiscloud.com/code/main.do?id=layer_request_boundary)
  * 모든 객체가 load 된 이후에 요청 제한 기능이 실행되어 즉각적으로 반영되도록 기능 개선하였습니다.

#### 4. JSPolygon.createTMCoordPlane API 오류 수정
  * 특정 유형 데이터에서 격자 밀림현상이 수정되었습니다.

Sure! Here's the English translation of the release notes:

---

### 2.16.1 (2025/07/15)

#### 1. High-Capacity 3DS Loading Optimization Feature Added

```javascript
var polygon = Module.createPolygon("POLYGON_3DS_LOAD");
	polygon.loadFile({
		url : _strURL,
		align : "center",
		position : pos,
		rotate :  fAngle,
		rebuild : true,
		discardVertexData : true,   // NEW: Discards vertex data after GPU upload
		compressObject : false,     // NEW: Do not compress vertex data after import
	});
```

#### 2. Cross-Section Edge Extraction Based on Building Height Added

* A function has been added to extract outer edge segments based on a specified building height.
* `object JSReal3D::getFloorSliceEdge(double _height)`
* Example return value:

```json
{
  "header": {
    // Minimum and maximum longitude/latitude of the data boundary
    "minLon": 126.927487351387,
    "minLat": 37.52418520251252,
    "maxLon": 126.92795509699533,
    "maxLat": 37.52453873807533,
    // Height at which the cross-section analysis is performed
    "cutHeight": 12.5,
    // Center point of the specified building
    "location": {
      "lon": 126.92774196141701,
      "lat": 37.52434050186833,
      "alt": 39.250494956970215
    },
    // Minimum and maximum elevation (altitude) of the building
    "elevation": {
      "min": 12.125300407409668,
      "max": 66.37568950653076
    }
  },
  // Cross-section edge data [Point A (lon, lat, alt) to Point B (lon, lat, alt)] [...] 
  "edge": [
    [
      126.9277111803299,
      37.52448908205179,
      22.275913742370903,
      126.927487351387,
      37.52435413856168,
      22.275933586061
    ],
    [
      126.9277111803299,
      37.52448908206028,
      22.27591446880251,
      126.92779354446381,
      37.524538738067506,
      22.27593025751412
    ],
    [ 
      ...
    ]
  ]
}
```


### 2.16.0 (2025/07/07)
#### 1. Camera Movement API Bug Fix

* [Camera Movement](https://sandbox.egiscloud.com/code/main.do?id=camera_set_viewrect)
* Fixed an issue where the camera was moving to an incorrect location instead of the specified position.

#### 2. POI Ahead Option Bug Fix

* [Object Ahead](https://sandbox.egiscloud.com/code/main.do?id=object_ahead)
* Fixed an issue where the POI ahead option was not functioning properly.

#### 3. Tile Layer Request Limitation Feature Improvement

* [Request Limit](https://sandbox.egiscloud.com/code/main.do?id=layer_request_boundary)
* Improved the feature so that the request limitation is applied immediately after all objects are loaded.

#### 4. JSPolygon.createTMCoordPlane API Bug Fix

* Fixed a grid displacement issue that occurred with certain types of data.


## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
