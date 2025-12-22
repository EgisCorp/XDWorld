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
- $\rm{\color{red}2.22.0\ 버전\ 배포는\ 1월\ 12일에\ 진행될\ 예정입니다.\ 참고\ 부탁드립니다.}$


### 2.21.0 (2025/12/01)
#### 1. 카메라 타겟 좌표 반환 API 추가
- 카메라 이동 애니메이션이 적용된 상태에서 카메라의 최종 목적지 좌표를 반환하는 API가 추가되었습니다.
```javascript
var pos = Module.getViewCamera().getTargetLocation();
```

#### 2. 카메라 플레이어 모드 추가
- 1인칭 카메라에 플레이어 모드(물리 기반)가 추가되었습니다.
- 이 모드에서는 점프 및 중력 낙하 효과가 자연스럽게 적용됩니다.
```javascript
var camera = Module.getViewCamera();
camera.setPlayerMode(true); // 플레이어 모드 활성화
camera.setPlayerMode(false); // 플레이어 모드 비활성화
```

#### 3. 카메라 점프 기능 API 추가
- 플레이어 모드에서 카메라가 점프 동작을 수행할 수 있는 API가 추가되었습니다.
- 점프 세기(jumpForce), 중력(gravity), 시간 간격(timeStep)을 조절할 수 있습니다.
- [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=camera_jump_outdoor)
```javascript
var camera = Module.getViewCamera();
camera.setJumpForce(30.0); // 기본값 10.0
camera.setGravity(9.8); // 기본값 9.8
camera.setTimeStep(0.06); // 기본값 0.05
camera.jump();
```

#### 4. 카메라 지면 감지 API 추가
- 1인칭 카메라가 현재 지면에 닿아 있는지 여부를 확인할 수 있는 API가 추가되었습니다.
- isGround()가 true일 때만 점프 기능이 동작합니다.
```javascript
var camera = Module.getViewCamera();
camera.isGround();
```

#### 5. 착지 고도 설정 API 추가
- 플레이어 모드에서 카메라의 착지 고도를 직접 지정할 수 있는 기능이 추가되었습니다.
- 특정 고도를 수동으로 설정하거나, 현재 위치의 지형 고도를 자동으로 적용할 수 있습니다.
```javascript
var camera = Module.getViewCamera();
camera.setLandingElevation(50.0); // 특정 고도를 착지 고도로 설정
camera.setLandingElevationToTerrain(); // 지형 고도를 착지 고도로 설정
```

#### 6. 카메라 범위 외 레이어 피킹 API 추가
- 기존에는 카메라 시야 영역 내 객체만 피킹이 가능했지만, 시야 영역에 관계없이 피킹이 가능한 API가 추가되었습니다.
```javascript
let buildingLayer = Module.getTileLayerList().nameAtLayer("facility_build");
pickPosition = buildingLayer.getPickInfoAtView(_from, _to); // 기존: 카메라 영역 내부만 피킹
pickPosition = buildingLayer.getPickInfo(_from, _to); // 추가: 카메라 영역 상관 없이 피킹
```

#### 7. 영역 내부의 건물 오브젝트 아이디 반환 API 추가
- 영역 내부의 건물 오브젝트 아이디를 반환하는 API가 추가되었습니다.
```javascript
var boundary = [
  [126.93790903169547, 37.522875202560655, 0.0],
  [126.92841620055285, 37.516978366894115, 0.0],
  [126.91894402430914, 37.52022975707285, 0.0]
] // 고도값 유무 상관 없음

var objects = Module.getTileLayerList().nameAtLayer("facility_build").getObjectsInBoundary(boundary);

console.log(objects.id);
```

#### 8. 3DTiles 요청 및 렌더링 최적화
- 3DTiles 요청시 SSE 기준 요청으로 변경
- 요청 순서 최적화
- 요청 수 관리로 브라우저 안정화

#### 9. 모바일 서비스 안정화

 -   일부 기기에서 POI 객체 선택시 오류 수정

#### 10. 선택된 객체 리스트 반환
- [선택된 객체 리스트 반환](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_select_info)

#### 11. 빌보드 객체 지형 아래 랜더링 오류 수정
- 빌보드 객체가 지형 아래로 내려가거나 걸칠경우 랜더링 되지 않는 현상 수정

### 2.21.0 (2025/11/03)
#### 1. Added API for Returning Camera Target Coordinates

* An API has been added to retrieve the final destination coordinates of the camera when a camera movement animation is in progress.

```javascript
var pos = Module.getViewCamera().getTargetLocation();
```

#### 2. Added Camera Player Mode

* A player mode (physics-based) has been added to the first-person camera.
* In this mode, natural jump and gravity effects are applied.

```javascript
var camera = Module.getViewCamera();
camera.setPlayerMode(true); // Enable player mode
camera.setPlayerMode(false); // Disable player mode
```

#### 3. Added Camera Jump API

* An API has been added that allows the camera to perform a jump action in player mode.
* You can adjust the jump force, gravity, and time step.
* [Sandbox sample](https://sandbox.egiscloud.com/code/main.do?id=camera_jump_outdoor)

```javascript
var camera = Module.getViewCamera();
camera.setJumpForce(30.0); // Default: 10.0
camera.setGravity(9.8); // Default: 9.8
camera.setTimeStep(0.06); // Default: 0.05
camera.jump();
```

#### 4. Added Camera Ground Detection API

* You can now check whether the first-person camera is currently touching the ground.
* The jump action works only when `isGround()` returns true.

```javascript
var camera = Module.getViewCamera();
camera.isGround();
```

#### 5. Added Landing Elevation API

* In player mode, you can manually set the camera’s landing elevation.
* You can set a specific elevation or automatically apply the terrain elevation at the current position.

```javascript
var camera = Module.getViewCamera();
camera.setLandingElevation(50.0); // Set a specific landing elevation
camera.setLandingElevationToTerrain(); // Apply terrain elevation as landing elevation
```

#### 6. Added Layer Picking API Outside Camera Range

* Previously, picking was only possible for objects within the camera’s view range.
  Now, an API allows picking regardless of camera visibility.

```javascript
let buildingLayer = Module.getTileLayerList().nameAtLayer("facility_build");
pickPosition = buildingLayer.getPickInfoAtView(_from, _to); // Previous: only within camera view
pickPosition = buildingLayer.getPickInfo(_from, _to); // New: pick regardless of camera range
```

#### 7. Added API for Returning Object IDs Inside a Boundary

* An API has been added to return the IDs of building objects located within a defined area.

```javascript
var boundary = [
  [126.93790903169547, 37.522875202560655, 0.0],
  [126.92841620055285, 37.516978366894115, 0.0],
  [126.91894402430914, 37.52022975707285, 0.0]
]; // Elevation is optional

var objects = Module.getTileLayerList().nameAtLayer("facility_build").getObjectsInBoundary(boundary);

console.log(objects.id);
```

#### 8. 3DTiles Request & Rendering Optimization

* Switched to SSE-based request handling for 3DTiles
* Optimized request order
* Stabilized browser performance through request count management

#### 9. Mobile Service Stabilization

* Fixed an issue where selecting POI objects on certain devices caused errors

#### 10. Added API for Retrieving Selected Object List

* [Get Select Object](https://sandbox-test.egiscloud.com/code/main.do?engine=latest&id=object_select_info)

#### 11. Fixed Billboard Rendering Issue Below Terrain

* Resolved an issue where billboard objects were not rendered when positioned below or intersecting with terrain

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
