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

### 2.29.3 (2026/08/28)
#### 1. GPU 외장, 내장 판단
  - True 반환 조건
    - 내장 GPU 사용중이고 외장 GPU가 있을 경우

  - False 반환 조건
    - 외장 GPU 사용중일 경우
    - GPU가 1개일 경우
    - 판별이 안될 경우

  - 기본적으로 True일 경우 console 창에 경고 로그 출력
  - `Module.isDiscreteGPUUnused();` API 사용하여 확인 가능
  - Engine Load 후 WebCode에서 메시지 창 띄우기 가능
 ```javascript
if (Module.gpuInfoReady) {
	Module.gpuInfoReady.then(function (info) {
		if (!info.needNotice) return;
		var head = (info.noticeLevel === "certain")
			? "이 PC에는 외장 그래픽카드가 있지만 현재 내장 그래픽(" + info.renderer + ")으로\n지도를 렌더링하고 있습니다."
			: "현재 내장 그래픽(" + info.renderer + ")으로 지도를 렌더링하고 있습니다.\n외장 그래픽카드가 있다면 아래 설정으로 성능을 높일 수 있습니다.";
		// 메시지창 띄우기
		alert(head + "\n\n" +
			"Windows 설정 > 시스템 > 디스플레이 > 그래픽 > 브라우저 추가 > 옵션 > '고성능'\n" +
			"선택 후 브라우저를 완전히 종료했다가 다시 실행해 주세요.");
	});
}
```

#### 2. Voxel 성능 향상
  -  사용방법은 샌드박스 샘플 참고
    - [Voxel](https://sandbox.egiscloud.com/code/main.do?id=effect_voxel)
    - [WildfireSpread](https://sandbox.egiscloud.com/code/main.do?id=analysis_wildfire_spread)
    - [typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typhoon)

#### 3. DataVisualizer Line 객체의 offset 설정 ([이슈 #586](https://github.com/EgisCorp/XDWorld/issues/586))
  - 동일한 위치로 겹치는 라인 간 z-fight 방지를 위하여 객체 간 offset 순서 설정

#### 4. Gaussian Splater
   - Gaussian Splatting 기능 추가
   - [Gaussian Splat](https://sandbox.egiscloud.com/code/main.do?&id=object_gaussian_splats)

#### 5. PlanerImage
   - 행성 이미지 적용 (달, 화성, 목성 등등)
   - [Planet Image](https://sandbox.egiscloud.com/code/main.do?&id=terrain_planet_image)

#### 6. 렌더링 후처리 기능 추가
   - 화면에 최종적으로 표출되는 씬이미지에 후처리를 통한 효과를 추가
   - JSPostProcess API 클래스 추가
   - 피사계심도 (DoF, Depth of Field) / Bloom / Sharpen 효과 추가
   - 주요 사용법은 [메뉴얼](https://github.com/avamk2/XDWorld_WebGL/issues/355#issue-5209387230) 및 [샌드박스 참고](https://sandbox.egiscloud.com/code/main.do?&id=postprocess_render_effect) 

#### 7. 투명도 (알파블랜딩) 개편
   - 기존 투명기능에서 투명객체의 정렬 문제로 표현되거나 사라지는 팝인 현상에 대한 개편
   - 사용법은 [샌드박스 참고](https://sandbox.egiscloud.com/code/main.do?&id=option_alphablend_mode)

#### 8. JSFlood z-fighting 현상 개선
  - 물판과 지형의 z-fighting 현상을 개선하였습니다.
  - 카메라 확대 시 물판이 사라지는 문제를 수정하였습니다.

#### 9. Impostor Rendering
  - 멀리 있는 3D 건물은 실제 3D 모델을 직접 렌더링하는 대신 Impostor로 대체하여 화면에 표현합니다. 이를 통해 복잡한 건물의 버텍스를 직접 렌더링하는 비용을 줄이고 전체적인 렌더링 성능을 향상시킬 수 있습니다.
  - Impostor 적용 조건은 다음과 같습니다.
    - 카메라 시점이 지면 기준 45° 이하로 낮게 눕혀진 경우
    - 해당 객체의 화면상 렌더링 크기가 64px 이하
    - 객체의 정점(Vertex) 수가 100pt 이상
  - 즉, 작게 보이면서 복잡한 3D 객체를 대상으로 실제 모델 대신 Impostor를 사용합니다.
  - 참고 : https://218.235.89.19:8443/tutorials/impostor/

#### 10. 레이어 타입에 상관없이 순서 변경 가능 [이슈 #587](https://github.com/EgisCorp/XDWorld/issues/587)
  - 기존에는 사용자 레이어끼리만 순서 변경이 가능하고 서비스 레이어끼리만 순서 변경이 가능
  - 레이어 타입에 상관없이 모든 레이어에 대해서 순서 변경 가능하도록 수정
   
#### 11. 수인한도분석 비동기 처리 [이슈 #589](https://github.com/EgisCorp/XDWorld/issues/589)
  - 기존에는 동기처리되어 분석 실행시 브라우저가 멈추는 현상 발생
  - 비동기 처리로 변경하여 분석 실행시 브라우저 멈추는 현상 없음

#### 12. 태양광 패널 배치 오류 수정 [이슈 #590](https://github.com/EgisCorp/XDWorld/issues/590)
  - 기존에는 건물타입 객체에만 생성 가능
  - 고스트심볼, GLTF, 3DS 등 다른 객체 타입에도 생성 가능하도록 수정

#### 13. Datavisualizer 데이터 오류 예외처리 [이슈 #594](https://github.com/EgisCorp/XDWorld/issues/594)
  - 기존에는 잘못된 데이터 좌표가 들어와도 수용하여 전체 객체에 영향을 미침
  - 잘못된 좌표가 들어와도 인스턴스 객체 중점 방식을 보완하여 다른 객체에 영향을 못 끼치도록 수정

#### 14. 객체 외곽선 랜더링 오류 수정 [이슈 #596](https://github.com/EgisCorp/XDWorld/issues/596)
  - 외곽선 생성 로직 누락되어 추가

#### 15. 서버기반 경사도,경사향,고도 분석 [이슈 #600](https://github.com/EgisCorp/XDWorld/issues/600)
  - 기존에는 화면에 로딩된 지형레벨에 대해서만 분석 가능
  - 로딩되지 않아도 분석 원하는 지형레벨에 대해서 분석 실행
  - 멀리서 또는 화면에 안보이는 지역에 대해서도 분석 가능

#### 16. 지형 편집 오류 수정 ([이슈 #593](https://github.com/EgisCorp/XDWorld/issues/593), [이슈 #599](https://github.com/EgisCorp/XDWorld/issues/599))
  - 서버 dem 레벨을 초과하는 지형에 대해 실시간 지형 편집 및 원복이 동작하지 않는 문제를 수정하였습니다.
  - 성토 시 사면이 생성되지 않는 오류를 수정하였습니다.
  - 바닥면이 주변 지형의 중간 높이로 설정되었을 때, 성절토가 동시에 적용될 수 있도록 개선하였습니다.


### 2.29.2 (2026/08/11)
#### 1. GLTF 모델 이동 위치 정보 갱신 개선 ([이슈 #580](https://github.com/EgisCorp/XDWorld/issues/580))
* GLTF 모델을 Trace Target으로 설정하여 이동할 때 내부 Bounding Box 위치가 갱신되지 않는 문제를 수정하였습니다.
* 이로 인해 model.position 및 model.getCenter()에서 실제 모델의 이동 위치가 정상적으로 반환되지 않는 문제를 수정하였습니다.

#### 2. 2D 가시권 분석 결과 갱신 API 추가 ([이슈 #581](https://github.com/EgisCorp/XDWorld/issues/581))
* 레이어의 가시성 변경 후 기존 2D 가시권 분석 결과를 현재 레이어 상태를 기준으로 다시 계산할 수 있는 updateViewshed() API를 추가하였습니다.
```javascript
buildingLayer.setVisible(false); // 레이어 가시성 변경
Module.getAnalysis().updateViewshed(); // 현재 레이어 상태 기준으로 가시권 재계산
```

#### 3. 3D 가시권 생성 동작 개선 ([이슈 #584](https://github.com/EgisCorp/XDWorld/issues/584))
* `setVFCreateClickMode(true)` 사용 시 드래그 동작에서 가시권이 생성되는 문제를 수정하였습니다.
* 단순 클릭 시에만 가시권이 생성되도록 동작을 개선하였습니다.

### 2.29.1 (2026/08/05)
#### 1. 사용자 레이어 객체 시점 이동 기능 개선
* 사용자 레이어 객체로 시점 이동이 간헐적으로 동작하지 않는 문제를 수정하였습니다.
* 사용자 레이어 객체로 시점 이동 시 바라보는 방향이 올바르게 설정되지 않는 문제를 수정하였습니다.

#### 2. 면적 측정 기능 개선
* `MML_ANALYS_AREA` 마우스 모드에서 면적 측정 시 폴리곤 및 외곽선이 지형에 결합되지 않는 문제를 수정하였습니다.

### 2.29.0 (2026/08/03)
#### 1. POI 텍스트 라벨링 및 아이콘 이미지 선명도 개선

#### 2. JSPolygon blob 방식 처리 추가 
   - JSPolygon::loadFile API에 data  속성을 통한 blob 처리 추가

```
async function load3DSa(_url, _position) {
    const response = await fetch(_url);
    if(response.ok == false) {
       throw new Error(
            `HTTP 오류: ${response.status} ${response.statusText}`
        );
    }
   const arrayBuffer = await response.arrayBuffer();
   let blob = new Uint8Array(arrayBuffer);
   // Create polygon layer
   var layerList = new Module.JSLayerList(true);
   var layer = layerList.createLayer("POLYGON_3DS_LAYER", Module.ELT_POLYHEDRON);
   var polygon = Module.createPolygon("POLYGON_3DS_LOAD");

   polygon.loadFile({
	type : "3ds",     // 3ds 포맷 명시
	position : _position,
	data : blob,      // fetch로 가져온 Uint8Array 버퍼
	align : "bottom",
	callback : function() {
		// Texture 로딩이 필요하면 기존방식 추가 처리 
		layer.addObject(polygon, 0);
	}
    });
    return polygon;
}
```

### 2.29.3 (2026/08/28)

#### 1. Discrete / Integrated GPU Detection
* Returns `true` under the following condition:
  * An integrated GPU is currently being used while a discrete GPU is available.
* Returns `false` under the following conditions:
  * A discrete GPU is currently being used.
  * Only one GPU is available.
  * GPU detection fails.
* By default, a warning message is printed to the console when the result is `true`.
* The GPU status can be checked using the `Module.isDiscreteGPUUnused();` API.
* A message dialog can be displayed in WebCode after the engine is loaded.

```javascript
if (Module.gpuInfoReady) {
	Module.gpuInfoReady.then(function (info) {
		if (!info.needNotice) return;
		var head = (info.noticeLevel === "certain")
			? "이 PC에는 외장 그래픽카드가 있지만 현재 내장 그래픽(" + info.renderer + ")으로\n지도를 렌더링하고 있습니다."
			: "현재 내장 그래픽(" + info.renderer + ")으로 지도를 렌더링하고 있습니다.\n외장 그래픽카드가 있다면 아래 설정으로 성능을 높일 수 있습니다.";
		// 메시지창 띄우기
		alert(head + "\n\n" +
			"Windows 설정 > 시스템 > 디스플레이 > 그래픽 > 브라우저 추가 > 옵션 > '고성능'\n" +
			"선택 후 브라우저를 완전히 종료했다가 다시 실행해 주세요.");
	});
}
```

#### 2. Voxel Performance Improvements
* Refer to the following Sandbox samples for usage:
  * [Voxel](https://sandbox.egiscloud.com/code/main.do?id=effect_voxel)
  * [WildfireSpread](https://sandbox.egiscloud.com/code/main.do?id=analysis_wildfire_spread)
  * [Typhoon](https://sandbox.egiscloud.com/code/main.do?id=weather_typhoon)

#### 3. Offset Setting for DataVisualizer Line Objects ([Issue #586](https://github.com/EgisCorp/XDWorld/issues/586))
* Added support for setting the offset order between overlapping line objects to prevent z-fighting.

#### 4. Gaussian Splatting
* Added Gaussian Splatting functionality.
* [Gaussian Splat](https://sandbox.egiscloud.com/code/main.do?&id=object_gaussian_splats)

#### 5. Planet Image
* Added support for applying planetary images, such as the Moon, Mars, and Jupiter.
* [Planet Image](https://sandbox.egiscloud.com/code/main.do?&id=terrain_planet_image)

#### 6. Post-Processing Effects
* Added post-processing effects to the final scene image displayed on the screen.
* Added the `JSPostProcess` API class.
* Added Depth of Field (DoF), Bloom, and Sharpen effects.
* For usage details, refer to the [Manual](https://github.com/avamk2/XDWorld_WebGL/issues/355#issue-5209387230) and [Sandbox sample](https://sandbox.egiscloud.com/code/main.do?&id=postprocess_render_effect).

#### 7. Alpha Blending Improvements
* Improved the existing transparency system to address pop-in issues where transparent objects could appear or disappear due to sorting problems.
* Refer to the [Sandbox sample](https://sandbox.egiscloud.com/code/main.do?&id=option_alphablend_mode) for usage details.

#### 8. JSFlood Z-Fighting Improvements
* Improved z-fighting issues between the water plane and terrain.
* Fixed an issue where the water plane disappeared when zooming in.

#### 9. Impostor Rendering
* Distant 3D buildings are rendered using Impostors instead of their original 3D models. This reduces the cost of rendering vertices from complex buildings and improves overall rendering performance.
* Impostors are applied under the following conditions:
  * The camera angle is 45° or lower relative to the ground.
  * The object's on-screen rendering size is 64 px or less.
  * The object has 100 or more vertices.
* In other words, Impostors are used for complex 3D objects that appear small on the screen.
* Reference: https://218.235.89.19:8443/tutorials/impostor/

#### 10. Layer Reordering Across Layer Types ([Issue #587](https://github.com/EgisCorp/XDWorld/issues/587))
* Previously, layer order could only be changed among user layers or among service layers.
* Updated to allow layer reordering regardless of layer type.

#### 11. Asynchronous Processing for Carrying Capacity Analysis ([Issue #589](https://github.com/EgisCorp/XDWorld/issues/589))
* Previously, the analysis was processed synchronously, causing the browser to become unresponsive during execution.
* Changed to asynchronous processing to prevent the browser from becoming unresponsive during analysis.

#### 12. Solar Panel Placement Error Fix ([Issue #590](https://github.com/EgisCorp/XDWorld/issues/590))
* Previously, solar panels could only be created on building-type objects.
* Updated to support creation on other object types, including Ghost Symbols, GLTF, and 3DS objects.

#### 13. DataVisualizer Data Error Handling ([Issue #594](https://github.com/EgisCorp/XDWorld/issues/594))
* Previously, invalid coordinate data was accepted and could affect the entire set of objects.
* Improved the instance object center-point handling so that invalid coordinates do not affect other objects.

#### 14. Object Outline Rendering Error Fix ([Issue #596](https://github.com/EgisCorp/XDWorld/issues/596))
* Added the missing outline generation logic.

#### 15. Server-Based Slope, Aspect, and Elevation Analysis ([Issue #600](https://github.com/EgisCorp/XDWorld/issues/600))
* Previously, analysis could only be performed on terrain levels currently loaded on the screen.
* Updated to allow analysis at the desired terrain level even when the terrain is not currently loaded.
* Analysis can now be performed on areas that are far away or not currently visible on the screen.

#### 16. Terrain Editing Error Fixes ([Issue #593](https://github.com/EgisCorp/XDWorld/issues/593), [Issue #599](https://github.com/EgisCorp/XDWorld/issues/599))
* Fixed an issue where real-time terrain editing and restoration did not work for terrain beyond the server DEM level.
* Fixed an issue where slopes were not generated during terrain filling.
* Improved terrain editing to allow cut and fill operations to be applied simultaneously when the bottom surface is set to the intermediate elevation of the surrounding terrain.

### 2.29.2 (2026/08/11)
#### 1. Improved GLTF Model Position Updates ([Issue #580](https://github.com/EgisCorp/XDWorld/issues/580))
* Fixed an issue where the internal Bounding Box position was not updated when moving a GLTF model set as the Trace Target.
* Fixed an issue where `model.position` and `model.getCenter()` did not return the actual position of the moved model.

#### 2. Added API for Updating 2D Viewshed Analysis Results ([Issue #581](https://github.com/EgisCorp/XDWorld/issues/581))
* Added the `updateViewshed()` API to recalculate existing 2D viewshed analysis results based on the current layer visibility state after changing layer visibility.

```javascript
buildingLayer.setVisible(false); // Change layer visibility
Module.getAnalysis().updateViewshed(); // Recalculate viewshed based on the current layer state
```

#### 3. Improved 3D Viewshed Creation Behavior ([Issue #584](https://github.com/EgisCorp/XDWorld/issues/584))
* Fixed an issue where a viewshed was created during a drag operation when using `setVFCreateClickMode(true)`.
* Improved the behavior so that a viewshed is created only when the user performs a simple click.

### 2.29.1 (2026/08/05)
#### 1. Improved Viewpoint Navigation for User Layer Objects

* Fixed an issue where viewpoint navigation to user layer objects would intermittently fail.
* Fixed an issue where the viewing direction was not set correctly when navigating to a user layer object.

#### 2. Improved Area Measurement

* Fixed an issue where the polygon and outline were not clamped to the terrain when performing area measurements in `MML_ANALYS_AREA` mouse mode.

### 2.29.0 (2026/08/03)
#### 1. Improved Sharpness of POI Text Labels and Icon Images

#### 2. Added Blob Support for `JSPolygon`

* Added support for loading polygon data from a blob via the `data` property in the `JSPolygon::loadFile` API.

```javascript
async function load3DSa(_url, _position) {
    const response = await fetch(_url);
    if(response.ok == false) {
       throw new Error(
            `HTTP Error: ${response.status} ${response.statusText}`
        );
    }

    const arrayBuffer = await response.arrayBuffer();
    let blob = new Uint8Array(arrayBuffer);

    // Create polygon layer
    var layerList = new Module.JSLayerList(true);
    var layer = layerList.createLayer("POLYGON_3DS_LAYER", Module.ELT_POLYHEDRON);
    var polygon = Module.createPolygon("POLYGON_3DS_LOAD");

    polygon.loadFile({
        type: "3ds",          // Specify the 3DS format
        position: _position,
        data: blob,           // Uint8Array buffer fetched via fetch()
        align: "bottom",
        callback: function() {
            // Add existing texture loading logic here if needed
            layer.addObject(polygon, 0);
        }
    });

    return polygon;
}
```

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
