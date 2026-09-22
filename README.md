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
> $\color{red}{\text{2.29.3 버전에서 worker 파일이 업데이트되었습니다.}}$<br>
> $\color{red}{\text{해당 버전 이상으로 업데이트 시 worker 업데이트가 필요합니다.}}$<br>
> $\color{red}{\text{XDWorldWorker.js 및 XDWorldWorker.wasm 파일을 엔진과 같이 배포된 파일로 교체해 주시기 바랍니다.}}$
> 
> $\color{red}{\text{The worker files have been updated in version 2.29.3.}}$<br>
> $\color{red}{\text{When updating to version 2.29.3 or later, a worker file update is required.}}$<br>
> $\color{red}{\text{Please replace XDWorldWorker.js and XDWorldWorker.wasm with the files distributed with the engine.}}$

> [!IMPORTANT]
> CDN 버전 정책이 변경되었습니다.
>
> 기존 `latest`(안정화 버전)는 `stable`로 대체되었습니다.
> 
> * `stable` : 안정화된 정기 배포 버전
> * `latest` : 최신 배포 버전 (핫픽스 포함)

### 2.30.2 (2026/09/22)
#### 1. 3D Tiles 관련 안정화 작업을 진행하였습니다.

### 2.30.1 (2026/09/14)
#### 1. 파티클 투명처리 오류 수정
  - 파티클 이미지의 투명 처리 추가
  - 처음 하나의 입자에만 크기, 속도 등 옵션 적용되던 현상 수정

#### 2. 불꽃 효과 추가
  - 불꽃축제 효과 추가
  - 불꽃 가시율 분석 추가
  - [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=effect_fireworks)

#### 3. 시곡면 분석 예외처리
  - 처음 분석 실행 후 같은 위치에 분석 실행 시 깜빡이는 현상 수정

#### 4. DataVisualizer 화면 고정 크기 모드 오류 수정 ([이슈 #614](https://github.com/EgisCorp/XDWorld/issues/614))
* 화면 고정 크기 모드 적용 시 뷰포트 사이즈에 따라 마커의 크기가 변하는 오류를 수정하였습니다.

#### 5. 폴리곤 객체 Clipping Box 기능 추가
* 폴리곤 객체를 잘라서 특정 부분만 렌더링 하는 기능을 추가하였습니다.
* MML_EDIT_CLIPPINGBOX 마우스 모드로 Clipping Box를 조작할 수 있습니다.
```javascript
Module.setClippingBoxPosition(new Module.JSVector3D(longitude, latitude, altitude));

Module.XDSetMouseState(Module.MML_EDIT_CLIPPINGBOX);
Module.setClippingBoxMode(0); // translate
// Module.setClippingBoxMode(2); // scale

var polygon = Module.createPolygon();
// ...
polygon.setClipping(true);
polygon.setClippingAlpha(0.3);
```

### 2.30.0 (2026/09/07)
#### 1. 그림자 효과 개선
  - 경계부분이 각져보이는 현상을 개선하였습니다.
  - 햇빛과 수평한 면에서 깜빡거리는 현상을 개선하였습니다.

#### 2. glTF 애니메이션 수정
  - 애니메이션 전환 시 애니메이션이 없는 노드는 원본 변환행렬을 사용하도록 수정하였습니다.

#### 3. 지형 편집 사면 RTT 영역 개선
  - 지형 편집의 사면에 대한 RTT 영역이 보다 정확하게 칠해지도록 개선하였습니다.

### 2.30.2 (2026/09/22)
#### 1. Improved the stability of 3D Tiles.

### 2.30.1 (2026/09/14)
#### 1. Particle Transparency Error Fix
* Added transparency support for particle images.
* Fixed an issue where options such as size and speed were applied only to the first particle.

#### 2. Firework Effect Added
* Added a fireworks effect.
* Added firework visibility analysis.

#### 3. Viewshed Analysis Exception Handling
* Fixed a flickering issue that occurred when running the analysis again at the same location after the initial analysis.

#### 4. DataVisualizer Screen-Fixed Size Mode Error Fix ([Issue #614](https://github.com/EgisCorp/XDWorld/issues/614))
* Fixed an issue where the marker size changed depending on the viewport size when Screen-Fixed Size Mode was applied.

#### 5. Clipping Box for Polygon Objects
* Added a feature to clip polygon objects and render only specific portions.
* The Clipping Box can be manipulated using the `MML_EDIT_CLIPPINGBOX` mouse mode.

```javascript
Module.setClippingBoxPosition(new Module.JSVector3D(longitude, latitude, altitude));

Module.XDSetMouseState(Module.MML_EDIT_CLIPPINGBOX);
Module.setClippingBoxMode(0); // translate
// Module.setClippingBoxMode(2); // scale

var polygon = Module.createPolygon();
// ...
polygon.setClipping(true);
polygon.setClippingAlpha(0.3);
```

### 2.30.0 (2026/09/07)
#### 1. Shadow Effect Improvements
* Improved the issue where shadow boundaries appeared jagged.
* Improved flickering on surfaces parallel to the sunlight.

#### 2. glTF Animation Fix
* Fixed the issue so that nodes without animations use their original transformation matrix when transitioning between animations.

#### 3. Improved RTT Area for Terrain Editing Slopes
* Improved the RTT area for terrain editing slopes to ensure more accurate rendering of the affected area.


---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
