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

### 2.27.1 (2026/06/08)
#### 1. skin 데이터 없는 glTF 애니메이션 지원
* skin 데이터가 포함되지 않은 glb/gltf 파일에서도 애니메이션이 정상적으로 재생되도록 수정하였습니다.

#### 2. glTF 애니메이션 속도 조절 API 추가
* 기존 프레임 기반으로 동작하던 애니메이션을 시간 기반으로 동작하도록 개선하였습니다.
* 애니메이션의 재생 속도를 제어할 수 있는 API를 추가하였습니다.
```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationSpeed(1.5); // default: 1.0
```

#### 3. CJSFigure::createPlane() uv 매핑 수정 ([Issue 555](https://github.com/EgisCorp/XDWorld/issues/555))
* CJSFigure::createPlane() 함수로 생성한 객체의 텍스처가 회전된 상태로 적용되는 문제를 수정하였습니다.

#### 4. glTF 다중 애니메이션 설정 API 추가
* 2개 이상의 애니메이션을 설정할 수 있는 API를 추가하였습니다.
```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationsByID([0, 1]);
```

### 2.27.0 (2026/06/01)
#### 1. voxel 인스턴싱 기능 추가 ([샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=analysis_wildfire_spread))
  - voxel 인스턴싱으로 여러개의 voxel 생성에도 성능이 유지됩니다.
  - Grid 데이터를 수용할 수 있도록 API를 추가하였습니다.(createGridVoxel, updateGridData)

#### 2. JSFigure 지형 편집 원복 함수 추가 ([issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* JSFigure 객체별로 Figure와 겹치는 영역의 편집을 원복할 수 있는 함수를 추가하였습니다.
```javascript
var fig = Module.createFigure("fig");
fig.setTexture();
fig.createOverlapRTT(true);

fig.undoEditTerrain();
```

#### 3. JSEditTerrain 지형 원복 오류 수정 ([issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* JSEditTerrain::clear(), JSEditTerrain::removeAtIndex() 함수 실행 시, 원복 대상 지형 이외의 지형에도 영향이 발생하는 문제를 수정하였습니다.
* CJSFigure::createOverlapRTT() 실행 시 다른 지형의 편집이 초기화되는 문제를 수정하였습니다.

#### 4. MML_ANALYS_DISTANCE_STRAIGHT 오류 수정 ([issue #556](https://github.com/EgisCorp/XDWorld/issues/556))
* MML_ANALYS_DISTANCE_STRAIGHT 마우스 모드에서 라인이 제대로 그려지지 않는 문제를 수정하였습니다.

#### 5. gltf, glb 텍스쳐 로드 콜백 ([issue #552](https://github.com/EgisCorp/XDWorld/issues/552))
* loadFile API를 통해 로드한 gltf, glb의 텍스쳐가 로딩 완료되었을 경우 콜백 함수가 호출되도록 기능을 추가하였습니다.
* 콜백 파라미터를 통해 텍스쳐 명칭(textureName) 및 전체 텍스쳐 수(textureTotalCount), 로드 된 텍스쳐 인덱스(textureIndex)를 조회하실 수 있습니다.
```javascript
polygon.loadFile({
  url : url,
  type : "glb",
  position : _position,
  callback : function(e) {
    console.log(e.textureName);
    console.log(e.textureTotalCount);
    console.log(e.textureIndex);
  }
});
```

#### 6. 타일레이어 기반 유저생성 폴리곤에 대한 그림자 렌더링 지원 ([issue #560](https://github.com/EgisCorp/XDWorld/issues/560))
* 유저생성 폴리곤 객체에서도 그림자 분석 처리가 가능하도록 수정하였습니다.

#### 7. 마우스 이벤트 처리 수정
* 마우스 드래그 상태로 지도 밖에 나간 후 버튼을 해제한 후에 다시 지도로 들어올 때 버튼을 놓아도 드래그로 인식한 문제를 수정하였습니다.
 
#### 8. 고스트심볼 Pitch, Yaw, Roll 회전 수정
* Yaw -> Pitch -> Roll 방식으로 회전축 변화에 맞게 수정하였습니다.

### 2.27.1 (2026/06/08)
#### 1. Support for glTF Animations Without Skin Data
* Fixed an issue where animations would not play correctly for GLB/glTF files that do not contain skin data.
* Animations can now be played properly even when skin data is absent.

#### 2. Added glTF Animation Speed Control API
* Improved the animation system to operate based on elapsed time rather than frame count.
* Added an API for controlling animation playback speed.
```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationSpeed(1.5); // default: 1.0
```

#### 3. Fixed UV Mapping in `CJSFigure::createPlane()` ([Issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* Fixed an issue where textures applied to objects created with `CJSFigure::createPlane()` appeared rotated.

#### 4. Added API for Multiple glTF Animations
* Added an API that allows multiple animations to be assigned simultaneously.
```javascript
var gltfObject = Module.createPolygon("GLTF_OBJECT");
gltfObject.setAnimationsByID([0, 1]);
```

### 2.27.0 (2026/06/01)
### 1. Added Voxel Instancing Feature ([Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?engine=latest&id=analysis_wildfire_spread))
* Added voxel instancing to maintain performance even when rendering a large number of voxels.
* Added APIs to support grid data: `createGridVoxel` and `updateGridData`.

### 2. Added Terrain Edit Revert Function for JSFigure ([Issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* Added a function that allows reverting terrain edits within the area overlapping a specific Figure object.
```javascript
var fig = Module.createFigure("fig");
fig.setTexture();
fig.createOverlapRTT(true);

fig.undoEditTerrain();
```

### 3. Fixed Terrain Reversion Issues in JSEditTerrain ([Issue #555](https://github.com/EgisCorp/XDWorld/issues/555))
* Fixed an issue where `JSEditTerrain::clear()` and `JSEditTerrain::removeAtIndex()` affected terrain areas outside the intended revert target.
* Fixed an issue where executing `CJSFigure::createOverlapRTT()` reset edits made to other terrain areas.

### 4. Fixed MML_ANALYS_DISTANCE_STRAIGHT Issue ([Issue #556](https://github.com/EgisCorp/XDWorld/issues/556))
* Fixed an issue where lines were not drawn correctly in the `MML_ANALYS_DISTANCE_STRAIGHT` mouse mode.

### 5. Added Texture Load Callback for glTF and GLB Models ([Issue #552](https://github.com/EgisCorp/XDWorld/issues/552))
* Added support for invoking a callback function when textures of glTF/GLB models loaded via the `loadFile` API have finished loading.
* The callback parameters provide access to the texture name (`textureName`), total texture count (`textureTotalCount`), and loaded texture index (`textureIndex`).
```javascript
polygon.loadFile({
  url : url,
  type : "glb",
  position : _position,
  callback : function(e) {
    console.log(e.textureName);
    console.log(e.textureTotalCount);
    console.log(e.textureIndex);
  }
});
```

### 6. Added Shadow Rendering Support for User-Created Polygons on Tile Layers ([Issue #560](https://github.com/EgisCorp/XDWorld/issues/560))
* Updated the engine to support shadow analysis for user-created polygon objects on tile layers.

### 7. Improved Mouse Event Handling
* Fixed an issue where dragging outside the map, releasing the mouse button, and then re-entering the map caused subsequent mouse actions to be incorrectly recognized as drag operations.

### 8. Updated Ghost Symbol Pitch, Yaw, and Roll Rotation Behavior
* Modified the rotation order to apply transformations in the sequence: **Yaw → Pitch → Roll**, ensuring rotations are applied correctly according to the changing axes.


---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
