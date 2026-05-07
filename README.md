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
- 다음 2.26.0 정기 업데이트는 5월 11일에 진행될 예정입니다.

> [!CAUTION]
> $\color{red}{\text{2.25.1 버전에서 worker 파일이 업데이트되었습니다.}}$<br>
> $\color{red}{\text{해당 버전 이상으로 업데이트 시 worker 업데이트가 필요합니다.}}$<br>
> $\color{red}{\text{XDWorldWorker.js 및 XDWorldWorker.wasm 파일을 엔진과 같이 배포된 파일로 교체해 주시기 바랍니다.}}$
> 
> $\color{red}{\text{The worker files have been updated in version 2.25.1.}}$<br>
> $\color{red}{\text{When updating to version 2.25.1 or later, a worker file update is required.}}$<br>
> $\color{red}{\text{Please replace XDWorldWorker.js and XDWorldWorker.wasm with the files distributed with the engine.}}$

### 2.26.0 (2026/05/08)
#### 1. 성절토 편집 렌더링 오류 수정 ([issue #557](https://github.com/EgisCorp/XDWorld/issues/557))
  * 성절토 편집 후 하위 타일들의 영상을 가져오지 않는 문제를 수정하였습니다.
  * 새로 로드된 하위 타일에 편집 내용이 적용되도록 개선하였습니다.

#### 2. 고스트 심볼 기능 업데이트 ([샌드박스 샘플](https://sandboxt.egiscloud.com/code/main.do?engine=latest_test&id=object_ghostsymbol_rotate_pyrl))
  - 심볼 모델포맷 GLB 추가 
      - JSGhostSymbolMap::addGhostSymbolByGLB( _key, _homeDir, _fileName)
      - addGhostSymbolBy3DS와 동일한 파라메터 속성 (_filename에 확장자 .glb는 제외)
  - 고스트심볼 객체에 Pitch, Yaw, Roll 회전을 설정 및 반환 기능 추가
      - JSGhostSymbol::getPitch(), getYaw(), getRoll() 로 각각 반환
      - JSGhostSymbol::setRotationPYR(_pitch, _yaw, _roll)로 설정


#### 3. 3D Line of Sight 커버리지 분석 기능 추가 ([샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest_test&id=analysis_lineofsightl))
  - 3D 방사형 LoS를 통한 가시/비가시 부분 분석 처리
  - JSON 옵션에 따른 분석방법 및 시각화 처리에 대한 조절가능

#### 4. voxel 기능 추가 ([샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=effect_voxel))
  - voxel 기능을 추가하여 3D texture로 다양한 효과 적용 가능

#### 5. datavisualizer 기능 추가 ([샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_point_datavisualizer), [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_point_datavisualizer_child), [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_line_datavisualizer), [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_line_symbol_datavisualizer))
  - Point, Line Type의 data 가시화
  - Child, Multi로 단계별 가시화 지원

#### 6. createOverlapRTT API 수정 ([issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
  - Figure객체 createOverlapRTT시 지형 업데이트 되지 않는 현상 수정

### 2.26.0 (2026/05/08)
#### 1. Fixed Terrain Cut/Fill Editing Rendering Issue ([issue #557](https://github.com/EgisCorp/XDWorld/issues/557))
* Fixed an issue where child tiles failed to load edited imagery after terrain cut/fill editing.
* Improved the system so that newly loaded child tiles correctly reflect the edited results.

#### 2. Ghost Symbol Feature Update ([Sandbox Sample](https://sandboxt.egiscloud.com/code/main.do?engine=latest_test&id=object_ghostsymbol_rotate_pyrl))
* Added support for the GLB model format for symbol models
  * `JSGhostSymbolMap::addGhostSymbolByGLB(_key, _homeDir, _fileName)`
  * Uses the same parameter properties as `addGhostSymbolBy3DS` (`_fileName` should exclude the `.glb` extension)
* Added Pitch, Yaw, and Roll rotation control and retrieval functions for ghost symbol objects
  * `JSGhostSymbol::getPitch()`, `getYaw()`, `getRoll()` return each rotation value
  * `JSGhostSymbol::setRotationPYR(_pitch, _yaw, _roll)` sets rotation values

#### 3. Added 3D Line of Sight Coverage Analysis Feature ([Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest_test&id=analysis_lineofsightl))
* Supports visible/non-visible area analysis using 3D radial LoS analysis
* Analysis methods and visualization options can be customized through JSON settings

#### 4. Added Voxel Feature ([Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=effect_voxel))
* Added voxel functionality to enable various effects using 3D textures

#### 5. Added DataVisualizer Feature ([Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_point_datavisualizer), [Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_point_datavisualizer_child), [Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_line_datavisualizer), [Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=object_line_symbol_datavisualizer))
* Supports visualization of Point and Line type data
* Supports hierarchical visualization through Child and Multi structures

#### 6. Updated `createOverlapRTT` API ([issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* Fixed an issue where terrain updates were not reflected when calling `createOverlapRTT` on Figure objects


---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
