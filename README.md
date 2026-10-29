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
> $\color{red}{\text{2.32.0 버전에서 worker 파일이 업데이트되었습니다.}}$<br>
> $\color{red}{\text{해당 버전 이상으로 업데이트 시 worker 업데이트가 필요합니다.}}$<br>
> $\color{red}{\text{XDWorldWorker.js 및 XDWorldWorker.wasm 파일을 엔진과 같이 배포된 파일로 교체해 주시기 바랍니다.}}$
> 
> $\color{red}{\text{The worker files have been updated in version 2.32.0.}}$<br>
> $\color{red}{\text{When updating to version 2.29.3 or later, a worker file update is required.}}$<br>
> $\color{red}{\text{Please replace XDWorldWorker.js and XDWorldWorker.wasm with the files distributed with the engine.}}$

> [!IMPORTANT]
> CDN 버전 정책이 변경되었습니다.
>
> 기존 `latest`(안정화 버전)는 `stable`로 대체되었습니다.
> 
> * `stable` : 안정화된 정기 배포 버전
> * `latest` : 최신 배포 버전 (핫픽스 포함)

### 2.32.0 (2026/11/02)
#### 1. Clipping Box 회전 기능 추가
- `Module.setGizmoMode(1);` 을 통해 Clipping Box를 회전할 수 있도록 기능을 추가하였습니다.

#### 2. 워커 CDN 경로 지원
- 워커 파일을 CDN 경로를 통해 요청할 수 있도록 기능을 추가하였습니다.
- 해당 기능은 **2.31.1 버전부터 지원합니다.**

#### 3. 하이브리드 레이어 최대 레벨 초과 시 하위 타일이 간헐적으로 표출되지 않던 현상 수정
  * `maxLevelOverlap: true` 사용 시 네트워크 지연으로 인해 하위 타일이 간헐적으로 만들어지지 않던 현상을 수정했습니다.

#### 4. 물 흐름 폴리곤 선택 시 외곽선 표출
  * 물 흐름 폴리곤(`createFlowPolygon`)을 선택하면 외곽선이 표시됩니다.
  * 외곽선 표시는 `setRenderSelectSilhouette` 옵션 설정을 따릅니다.

#### 5. 물 흐름 폴리곤 지형 영상 표출 시 폴리곤 경계에서 영상이 어긋나던 현상 수정
  * `image_type = 3`(지형 영상) 사용 시 인접한 폴리곤의 경계에서 영상이 끊겨 보이던 현상을 수정했습니다.

#### 6. 물 흐름 폴리곤 지형 영상 표출 성능 개선
  * `image_type = 3`(지형 영상) 사용 시 지형이 바뀌지 않는 동안에는 지형을 다시 그리지 않도록 개선했습니다. 폴리곤이 많은 장면에서 렌더링 부하가 줄어듭니다.

#### 7. 3D Tiles `지형 가림 해제` 기능 추가
- 메시·스플랫·점구름이 그려진 화면 영역에서만 지형을 그리지 않습니다. 지형에 묻힌 자료도 그대로 보입니다.
- 새 API는 다음과 같습니다. 전역 스위치와 레이어 스위치가 둘 다 켜져야 동작하고, 기본값은 꺼짐이라 기존 화면에는 영향이 없습니다.
    - 전역: Module.XDESetTerrainMask(true/false), Module.XDEGetTerrainMask()
    - 레이어: layer.setTileTerrainMask(true/false), layer.getTileTerrainMask()
<table>
  <tr>
    <th>지형 가림 해제 끔 (메시를 30 m 묻은 화면)</th>
    <th>지형 가림 해제 켬</th>
  </tr>
  <tr>
    <td><img src="https://github.com/avamk2/XDWorld_WebGL/releases/download/pr-assets/terrain-mask-before.png" width="100%"></td>
    <td><img src="https://github.com/avamk2/XDWorld_WebGL/releases/download/pr-assets/terrain-mask-after.png" width="100%"></td>
  </tr>
</table>

#### 8. 조류흐름 방식 개선
- 웹에서 png 생성 후 전달하는 방식에서 배열 전달 방식으로 변경
- 엔진 내부에서 배열로 조류 흐름 가시화

#### 9. 지구본 로드시 z-fighting 현상 수정

#### 10. 후처리 효과 추가 - (https://sandbox.egiscloud.com/code/main.do?id=postprocess_render_effect)
- SSAO 옵션 추가
- Screen Space Fog 옵션

#### 11. 장면기반 환경효과 추가 - (https://sandbox.egiscloud.com/code/main.do?id=postprocess_render_effect)
 - 시간대별 밤,낮,일조,일몰 환경표현 및 3D모델 그림자 연동
 - 맑음, 흐림, 비, 눈, 뇌우 기반 환경효과 적용


### 2.32.0 (2026/11/02)
#### 1. Added Clipping Box Rotation Feature
- Added functionality to rotate Clipping Boxes via `Module.setGizmoMode(1);`.

#### 2. Added Worker CDN Path Support
- Added support for requesting worker files via CDN paths.
- This feature is **supported starting from version 2.31.1.**

#### 3. Fixed Issue Where Sub-tiles Were Intermittently Not Displayed When Exceeding Hybrid Layer Max Level
  * Fixed an issue where sub-tiles were intermittently not generated due to network delays when using `maxLevelOverlap: true`.

#### 4. Displayed Outlines When Selecting Water Flow Polygons
  * Outlines are now displayed when a water flow polygon (`createFlowPolygon`) is selected.
  * Outline rendering follows the `setRenderSelectSilhouette` option setting.

#### 5. Fixed Discontinuous Imagery at Water Flow Polygon Boundaries
  * Fixed an issue where imagery appeared misaligned at the boundaries of adjacent polygons when using `image_type = 3` (terrain imagery).

#### 6. Improved Rendering Performance for Water Flow Polygon Terrain Imagery
  * Improved rendering performance so that terrain is not redrawn while the terrain remains unchanged when using `image_type = 3` (terrain imagery). This reduces rendering load in scenes with many polygons.

#### 7. Added 3D Tiles `Disable Terrain Occlusion` Feature
- Hides terrain only in screen areas where meshes, splats, or point clouds are rendered. Data buried beneath the terrain remains visible.
- The new APIs are as follows. Both the global switch and layer switch must be enabled to operate. The default value is off, preserving existing displays.
    - Global: Module.XDESetTerrainMask(true/false), Module.XDEGetTerrainMask()
    - Layer: layer.setTileTerrainMask(true/false), layer.getTileTerrainMask()
<table>
  <tr>
    <th>Disable Terrain Occlusion Off (Mesh buried by 30 m)</th>
    <th>Disable Terrain Occlusion On</th>
  </tr>
  <tr>
    <td><img src="https://github.com/avamk2/XDWorld_WebGL/releases/download/pr-assets/terrain-mask-before.png" width="100%"></td>
    <td><img src="https://github.com/avamk2/XDWorld_WebGL/releases/download/pr-assets/terrain-mask-after.png" width="100%"></td>
  </tr>
</table>

#### 8. Improved Tidal Flow Processing
- Changed the implementation from passing web-generated PNGs to passing arrays directly.
- Visualizes tidal flow internally within the engine using arrays.

#### 9. Fixed Z-fighting Issue During Globe Loading

#### 10. Added Post-Processing Effects - (https://sandbox.egiscloud.com/code/main.do?id=postprocess_render_effect)
- Added SSAO option
- Added Screen Space Fog option

#### 11. Added Scene-Based Environmental Effects - (https://sandbox.egiscloud.com/code/main.do?id=postprocess_render_effect)
 - Added environmental rendering for day, night, sunrise, and sunset by time of day, integrated with 3D model shadows
 - Applied environmental effects for clear, cloudy, rainy, snowy, and thunderstorm conditions

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
