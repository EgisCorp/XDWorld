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
- 2.31.0 버전 정기 배포는 10월 6일에 진행될 예정입니다.

> [!CAUTION]
> $\color{red}{\text{2.30.2 버전에서 worker 파일이 업데이트되었습니다.}}$<br>
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

### 2.31.0 (2026/10/06)
#### 1. 기즈모 Scale 모드 추가
- 스케일을 조절하는 기즈모 모드가 추가되었습니다.
```javascript
Module.setGizmoMode(2); // scale
```

#### 2. moveWithSlide API 추가
- 1인칭 카메라 이동 시 벽면에 충돌했을 경우 자연스럽게 미끌어져 이동하는 API가 추가되었습니다. ([샘플](https://sandbox.egiscloud.com/code/main.do?id=camera_jump_Indoor))

#### 3. Clipping Box 조작 방식 변경
- Clipping Box를 기즈모를 통해 조작할 수 있도록 변경하였습니다. ([샘플](https://sandbox.egiscloud.com/code/main.do?id=object_clippingbox))
```javascript
Module.XDSetMouseState(Module.MML_EDIT_CLIPPINGBOX);
Module.setGizmoMode(0); // translate
// Module.setGizmoMode(1); // rotate(현재 미구현)
// Module.setGizmoMode(2); // scale
```

#### 4. 3D 타일 레이어 로딩 성능 개선 ([이슈 #620](https://github.com/EgisCorp/XDWorld/issues/620))
- 현재 화면에서 요청할 타일이 없는 3D 타일 레이어가 요청 처리 순서에 포함되어 다른 레이어의 타일 로딩이 지연되는 문제를 수정하였습니다.

####  5. 피킹 수정
- 자식 노드에 객체가 있으면 부모 객체를 통째로 후보에서 빼던 조건을 제거했습니다. 화면에 보이는 건물이 선택되지 않던 증상이 사라집니다. (API 변경 없음)

#### 6. 자동 메모리 정리의 주기 조정 API 추가
- XDESetMemoryClearInterval(ms) / XDEGetMemoryClearInterval() → number 
- 엔진 자동 메모리 정리의 주기를 밀리초로 지정합니다. 기존에는 상수였던 값을 런타임에 바꿀 수 있게 한 것으로, 재빌드 없이 여러 값을 같은 세션에서 비교할 때 씁니다.
#### Information

| Name | Type   | Required | Description                                               |
| ---- | ------ | -------- | --------------------------------------------------------- |
| ms   | number | ✔        | 정리 주기(밀리초). 기본 5000. 0이면 매 프레임 정리합니다. 음수는 0으로 처리합니다.      |

* Return
  * `XDESetMemoryClearInterval` → 없음.
  * `XDEGetMemoryClearInterval` → number. 현재 주기(ms).
* 참고
  * **0은 진단용입니다.** 매 프레임 정리는 비용이 커서 상시로 쓸 값이 아닙니다 — 누수가 정리 주기 때문인지 가릴 때만 씁니다.
  * 주기를 늘리면 정리 호출은 줄지만 그동안 해제가 밀려 메모리 고점이 올라갑니다.

#### Template

```javascript
// 2초마다 정리
Module.XDESetMemoryClearInterval(2000);

var ms = Module.XDEGetMemoryClearInterval();
// ms → 2000

// 진단: 매 프레임 정리해도 메모리가 계속 오르면 정리 주기가 원인이 아니다
Module.XDESetMemoryClearInterval(0);
```

### 7. 라벨 POI 아틀라스를 지원합니다.
- XDECreateLabelAtlas(data, width, height) → number
  - 라벨 여러 개를 담은 이미지 한 장을 GPU 텍스처로 올리고 아틀라스 ID를 돌려줍니다. 이후 `JSPoint.setImageAtlas()`로 각 포인트가 이 텍스처의 한 칸만 참조하므로, 라벨마다 텍스처를 만들고 업로드하던 비용이 사라집니다.
- XDEReleaseLabelAtlas(atlasId) → boolean
  - 아틀라스를 레지스트리에서 제거합니다. 이미 `setImageAtlas()`로 붙여 둔 포인트가 있으면 GPU 텍스처는 그대로 살아 있고, 마지막 포인트가 사라질 때 함께 해제됩니다(참조 계수).
- JSPoint.setImageAtlas(atlasId, x, y, width, height) → boolean
  - 아틀라스의 한 칸을 이 포인트의 심볼로 지정합니다. 픽셀 좌표는 아틀라스 이미지 기준입니다. 텍스처를 새로 만들지 않고 기존 아틀라스 텍스처를 참조만 하므로, 포인트가 늘어나도 텍스처 개수와 업로드 횟수는 그대로입니다.

### 8. 팔레트 256컬러 라벨을 지원합니다.
- XDESetPoiTexture8Bit(on) / XDEGetPoiTexture8Bit() → boolean 
  - POI 라벨 텍스처를 8비트 팔레트(PAL8)로 저장합니다. 픽셀당 1바이트 인덱스 + 공용 팔레트 아틀라스 행 구조라, 라벨 텍스처 메모리가 절반 이하로 줄어듭니다(실측 라벨당 7,893B → 3,947B). **기본 꺼짐**입니다.

- XDEGetPoiTexture8BitStats() → object
  - PAL8 변환의 왕복 검증 장부와 팔레트 아틀라스 상태를 돌려줍니다. **진단 전용**입니다 — 라벨이 깨져 보일 때 원인이 양자화인지 폴백인지 가릅니다.


### 2.31.0 (2026/10/06)
#### 1. Added Gizmo Scale Mode
* Added a Gizmo mode for scaling objects.

```javascript
Module.setGizmoMode(2); // scale
```

#### 2. Added `moveWithSlide` API
* Added an API that allows first-person camera movement to naturally slide along a wall when a collision occurs. ([Sample](https://sandbox.egiscloud.com/code/main.do?id=camera_jump_Indoor))

#### 3. Changed Clipping Box Manipulation
* Changed the Clipping Box so that it can be manipulated using the Gizmo. ([Sample](https://sandbox.egiscloud.com/code/main.do?id=object_clippingbox))

```javascript
Module.XDSetMouseState(Module.MML_EDIT_CLIPPINGBOX);
Module.setGizmoMode(0); // translate
// Module.setGizmoMode(1); // rotate (not implemented)
// Module.setGizmoMode(2); // scale
```

#### 4. Improved 3D Tile Layer Loading Performance ([Issue #620](https://github.com/EgisCorp/XDWorld/issues/620))
* Fixed an issue where 3D tile layers with no tiles to request in the current view were included in the request queue, delaying tile loading for other layers.

#### 5. Picking Improvements
* Removed the condition that excluded the entire parent object from the picking candidates when an object existed in a child node.
* This fixes an issue where visible buildings could not be selected.
* No API changes.

#### 6. Added API to Adjust the Automatic Memory Cleanup Interval
* `XDESetMemoryClearInterval(ms)` / `XDEGetMemoryClearInterval()` → `number`
* Allows the interval of the engine's automatic memory cleanup to be specified in milliseconds.
* The interval was previously fixed as a constant and can now be changed at runtime, allowing different values to be compared within the same session without rebuilding the engine.

#### Information
| Name | Type   | Required | Description                                                                                                                      |
| ---- | ------ | -------- | -------------------------------------------------------------------------------------------------------------------------------- |
| ms   | number | ✔        | Cleanup interval (milliseconds). Default: 5000. If set to 0, cleanup is performed every frame. Negative values are treated as 0. |

* Return
  * `XDESetMemoryClearInterval` → None.
  * `XDEGetMemoryClearInterval` → `number`. Current interval (ms).
* Notes
  * **0 is intended for diagnostic purposes.** Performing cleanup every frame can be expensive and should not be used continuously. Use it only when determining whether memory growth is caused by the cleanup interval.
  * Increasing the interval reduces the frequency of cleanup calls, but memory may remain allocated longer, resulting in a higher peak memory usage.

#### Template
```javascript
// Cleanup every 2 seconds
Module.XDESetMemoryClearInterval(2000);

var ms = Module.XDEGetMemoryClearInterval();
// ms → 2000

// Diagnostic: If memory continues to increase even with cleanup every frame,
// the cleanup interval is not the cause.
Module.XDESetMemoryClearInterval(0);
```

### 7. Added Support for Label POI Atlases
* `XDECreateLabelAtlas(data, width, height)` → `number`
  * Uploads an image containing multiple labels as a single GPU texture and returns the atlas ID.
  * Each point can then reference a specific region of this texture using `JSPoint.setImageAtlas()`, eliminating the cost of creating and uploading a separate texture for each label.

* `XDEReleaseLabelAtlas(atlasId)` → `boolean`
  * Removes the atlas from the registry.
  * If there are points that have already been assigned the atlas using `setImageAtlas()`, the GPU texture remains alive and is released when the last referencing point is removed through reference counting.

* `JSPoint.setImageAtlas(atlasId, x, y, width, height)` → `boolean`
  * Specifies a region of the atlas as the symbol for the point.
  * Pixel coordinates are based on the atlas image.
  * Since the point references the existing atlas texture without creating a new texture, the number of textures and texture uploads remains unchanged even as the number of points increases.

### 8. Added Support for 256-Color Palette Labels

* `XDESetPoiTexture8Bit(on)` / `XDEGetPoiTexture8Bit()` → `boolean`
  * Stores POI label textures using an 8-bit palette (PAL8).
  * Since each pixel uses a 1-byte index and a shared palette-atlas row structure, label texture memory usage is reduced by more than half (measured from 7,893 B to 3,947 B per label).
  * **Disabled by default.**

* `XDEGetPoiTexture8BitStats()` → `object`
  * Returns diagnostic information for round-trip validation of the PAL8 conversion and the current state of the palette atlas.
  * **For diagnostic purposes only.** Helps determine whether visual corruption of labels is caused by quantization or fallback processing.

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
