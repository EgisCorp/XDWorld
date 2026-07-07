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

> [!CAUTION]
> $\color{red}{\text{2.25.1 버전에서 worker 파일이 업데이트되었습니다.}}$<br>
> $\color{red}{\text{해당 버전 이상으로 업데이트 시 worker 업데이트가 필요합니다.}}$<br>
> $\color{red}{\text{XDWorldWorker.js 및 XDWorldWorker.wasm 파일을 엔진과 같이 배포된 파일로 교체해 주시기 바랍니다.}}$
> 
> $\color{red}{\text{The worker files have been updated in version 2.25.1.}}$<br>
> $\color{red}{\text{When updating to version 2.25.1 or later, a worker file update is required.}}$<br>
> $\color{red}{\text{Please replace XDWorldWorker.js and XDWorldWorker.wasm with the files distributed with the engine.}}$

> [!IMPORTANT]
> CDN 버전 정책이 변경되었습니다.
>
> 기존 `latest`(안정화 버전)는 `stable`로 대체되었습니다.
> 
> * `stable` : 안정화된 정기 배포 버전
> * `latest` : 최신 배포 버전 (핫픽스 포함)

### 2.28.1 (2026/07/07)
#### 1. 3DTiles 안정화 작업을 수행하였습니다.

### 2.28.0 (2026/07/06)
#### 1. JSPolygon getCoordinates API 기능 개선([이슈 #569](https://github.com/EgisCorp/XDWorld/issues/569))
  - JSPolygon의 `move`, `moveAltitude`, `setRotate`, `setScale` API를 통해 좌표가 변경된 경우 getCoordinates로 반환되는 좌표 값이 갱신되도록 기능을 개선하였습니다.

#### 2. Catmull-Rom 곡선 생성 API 추가
* 모든 입력 좌표를 지나는 부드러운 곡선을 생성할 수 있는 API가 추가되었습니다.
  * 기존 베지어 곡선 생성 API는 시작점과 끝점을 제외한 나머지 점들은 곡선이 지나지 않습니다. 
* 내비게이션 및 카메라 이동 경로 생성에 적합합니다.

```javascript
var coord = [
  [lon, lat, alt],
  [lon, lat, alt],
  // ...
  [lon, lat, alt]
];

var parameters = {
  coordinates : {
    coordinate : coord,
    style : "XYZ"
  },
  alpha: 0.5,     // default: 0.0 (0~1, 곡선의 안정성. 0.5일 때 가장 안정적)
  tension: 0.5,   // default: 0.0 (0~1, 값이 클수록 직선에 가까워짐)
  samples: 10,    // default: 20 (구간당 생성할 샘플 좌표 수)
  simplify: true, // default: false (근접 좌표 단순화 적용 여부)
  epsilon: 0.5,   // default: 0.5 (simplify 적용 시 단순화 거리 임계값)
  union: true,    // default: false (지형 결합 여부)
  height: 1.5     // default: 0.0 (지형 결합 시 지형으로부터의 높이)
}

var catmullrom = Module.getMath().convertCatmullRom(parameters);
var catmullrom.position // 좌표
var catmullrom.times    // 누적 거리
```

### 2.28.1 (2026/07/07)
#### 1. Improved the stability of 3D Tiles.

### 2.28.0 (2026/07/06)
#### 1. Improved `JSPolygon.getCoordinates` API ([Issue #569](https://github.com/EgisCorp/XDWorld/issues/569))
* Improved the `JSPolygon.getCoordinates` API so that it now returns updated coordinate values after the polygon has been modified using the `move`, `moveAltitude`, `setRotate`, or `setScale` APIs.

#### 2. Added Catmull-Rom Curve Generation API
* Added a new API for generating smooth Catmull-Rom curves that pass through all input coordinates.
  * Unlike the existing Bézier curve generation API, which only guarantees that the curve passes through the start and end points, the Catmull-Rom curve passes through every input point.
* This API is well suited for navigation routes and camera path generation.

```javascript
var coord = [
  [lon, lat, alt],
  [lon, lat, alt],
  // ...
  [lon, lat, alt]
];

var parameters = {
  coordinates: {
    coordinate: coord,
    style: "XYZ"
  },
  alpha: 0.5,     // default: 0.0 (range: 0–1, controls curve stability; 0.5 provides the most stable result)
  tension: 0.5,   // default: 0.0 (range: 0–1, higher values produce a straighter curve)
  samples: 10,    // default: 20 (number of sample points generated per segment)
  simplify: true, // default: false (whether to simplify nearby coordinates)
  epsilon: 0.5,   // default: 0.5 (distance threshold used when simplification is enabled)
  union: true,    // default: false (whether to clamp the curve to the terrain)
  height: 1.5     // default: 0.0 (height above the terrain when terrain clamping is enabled)
};

var catmullrom = Module.getMath().convertCatmullRom(parameters);
var catmullrom.position; // Generated coordinates
var catmullrom.times;    // Cumulative distances
```


---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
