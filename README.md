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
