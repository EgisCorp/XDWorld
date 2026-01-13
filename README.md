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

- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.


### 2.22.0 (2026/01/12)
#### 1. 시곡면 분석 정확도 향상
  - [시곡면 분석](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_height_regulation) 정확도 향상 및 0~360도 범위 확장
<img width="916" height="690" alt="image" src="https://github.com/user-attachments/assets/f091e9f7-1fd9-4a67-8dd6-f2d738cdfd96" />

#### 2. 1인칭 카메라 비디오 텍스쳐 기능 지원 중단
  - 기존 1인칭 카메라 비디오 텍스쳐 기능은 2025년까지 지원합니다. 
  - JSCamera 클래스의 삭제 API ---------> JSVideoObject 클래스의 대체 API 
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

  - 비디오 객체  [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

#### 3. 건물 레이어 limit boundary 옵션 추가
  * 건물 레이어 boundaryLimit에 mode: "exclude" 옵션을 추가해 경계 내부를 제외하고 외부 오브젝트만 로드할 수 있도록 개선했습니다.
  * 아래와 같이 설정하는 경우 바운더리 외 건물이 로드됩니다.
    ``` javascript
    const boundary = [
          [126.93005255915998, 37.529214172573376],
          [126.94102835336719, 37.52029412432422],
          [126.93891529125652, 37.51798498831805],
          [126.92841620055285, 37.516978366894115],
          [126.92514862234246, 37.51770012779483],
          [126.91756299430655, 37.521708873949606],
    ];

    Module.getTileLayerList().createXDServerLayer({
          ...
          boundaryLimit: {
            mode: "exclude",
            rings: boundary
          }
    });
    ```
  * 아래와 같이 설정하는 경우 바운더리 내부 건물만 로드됩니다. (기존 방식과 동일)
    ``` javascript
    const boundary = [
          [126.93005255915998, 37.529214172573376],
          [126.94102835336719, 37.52029412432422],
          [126.93891529125652, 37.51798498831805],
          [126.92841620055285, 37.516978366894115],
          [126.92514862234246, 37.51770012779483],
          [126.91756299430655, 37.521708873949606],
    ];

    Module.getTileLayerList().createXDServerLayer({
          ...
          boundaryLimit: {
            mode: "include",
            rings: boundary
          }
    });
    ```
* exclude/include 옵션이 없는 경우 include 타입으로 자동 지정되어 바운더리 내부 건물만 로드됩니다.

#### 4. 엔진 상태 체크 옵션 추가
```javascript
Module.initialize({
	.
	.
	.
	ping: enginePing
});

function enginePing(e) {
	console.log(e);
}
```

#### 5. 수평 이동 위치 반환 API 추가
* 전후좌우 방향으로 특정 거리만큼 수평 이동한 좌표를 반환하는 API가 추가되었습니다.
  ```javascript
  var camera = Module.getViewCamera();
  camera.getPanMoveLocation(moveType, distance);
  // moveType : 0(front), 1(back), 2(left), 3(right)
  ```

#### 6. 1인칭 카메라 모드 높이 설정 API 추가
* 1인칭 카메라 모드에서 카메라의 높이를 설정하는 API가 추가되었습니다.
  ```javascript
  var camera = Module.getViewCamera();
  camera.setPersonHeight(1.5);
  ```

#### 7. 플레이어 모드 천장 설정 API 추가
* 플레이어 모드에서 천장 고도를 설정하여 점프 시 천장에 부딪히도록 하는 API가 추가되었습니다.
  ```javascript
  var camera = Module.getViewCamera();
  camera.setCeiling() // 천장 설정 해제
  camera.setCeiling(10.0); // 천장 고도 설정
  ```

### 2.22.0 (2026/01/12)
#### 1. Improved Accuracy of Sky View (View-Shed) Analysis
  - Improved accuracy of the [Sky View Analysis](https://sandbox.egiscloud.com/code/main.do?id=analysis_building_height_regulation) and expanded the angle range to 0–360 degrees.
<img width="916" height="690" alt="image" src="https://github.com/user-attachments/assets/f091e9f7-1fd9-4a67-8dd6-f2d738cdfd96" />

#### 2. Deprecation of First-Person Camera Video Texture
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

#### 3. Added limit boundary Option for Building Layers
  * A new `mode: "exclude"` option has been added to `boundaryLimit`, allowing only objects outside the boundary to be loaded.
  * With the following setting, buildings outside the boundary will be loaded.
    ```javascript
    const boundary = [
          [126.93005255915998, 37.529214172573376],
          [126.94102835336719, 37.52029412432422],
          [126.93891529125652, 37.51798498831805],
          [126.92841620055285, 37.516978366894115],
          [126.92514862234246, 37.51770012779483],
          [126.91756299430655, 37.521708873949606],
    ];

    Module.getTileLayerList().createXDServerLayer({
          ...
          boundaryLimit: {
            mode: "exclude",
            rings: boundary
          }
    });
    ```
  * With the following setting, only buildings inside the boundary will be loaded (same as the existing behavior).
    ```javascript
    const boundary = [
          [126.93005255915998, 37.529214172573376],
          [126.94102835336719, 37.52029412432422],
          [126.93891529125652, 37.51798498831805],
          [126.92841620055285, 37.516978366894115],
          [126.92514862234246, 37.51770012779483],
          [126.91756299430655, 37.521708873949606],
    ];

    Module.getTileLayerList().createXDServerLayer({
          ...
          boundaryLimit: {
            mode: "include",
            rings: boundary
          }
    });
    ```
* If no `exclude/include` option is specified, it defaults to `include` and only buildings inside the boundary will be loaded.

#### 4. Added Engine Status Check Option
```javascript
Module.initialize({
	.
	.
	.
	ping: enginePing
});

function enginePing(e) {
	console.log(e);
}
```

#### 5. Added Horizontal Movement Position API

* An API has been added that returns the coordinates after moving a certain distance horizontally (front, back, left, or right).

  ```javascript
  var camera = Module.getViewCamera();
  camera.getPanMoveLocation(moveType, distance);
  // moveType : 0(front), 1(back), 2(left), 3(right)
  ```

#### 6. Added First-Person Camera Height API

* An API has been added to set the camera height in first-person camera mode.

  ```javascript
  var camera = Module.getViewCamera();
  camera.setPersonHeight(1.5);
  ```

#### 7. Added Player Mode Ceiling API

* An API has been added to set the ceiling altitude in player mode so the player collides with the ceiling when jumping.

  ```javascript
  var camera = Module.getViewCamera();
  camera.setCeiling();      // Disable ceiling
  camera.setCeiling(10.0);  // Set ceiling height
  ```

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
