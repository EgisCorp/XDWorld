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

### 2.19.0 (2025/10/13)
#### 1. 오버레이 기능 오류 수정 [(이슈 #513)](https://github.com/EgisCorp/XDWorld/issues/513)
 * 간헐적으로 검은색 이미지가 오버레이 되는 현상이 수정되었습니다.
 * 이미지 오버레이 투명값 옵션이 추가되었습니다.
 ```javascript
polygon.setOverlayObject({
	style : "polygon",
	coordinate : vertex,
	alpha : 0.6,           // 추가된 옵션
	image : _image
});
 ```
 * 건물 심플모드에 오버레이 적용되지 않는 현상 수정
건물 외곽선 렌더링을 원하지 않을 경우 : Module.SetSimpleModeLineRender(false);
<img width="969" height="690" alt="image" src="https://github.com/user-attachments/assets/d4d0761e-c7b2-437e-a3d5-6eedbf4965bf" />

#### 2. 라인객체 GLOW 효과 개선
 * 기존 GLOW 효과를 개선하였습니다.
<img width="645" height="619" alt="image" src="https://github.com/user-attachments/assets/c4dde99b-8e5d-48d9-a5d9-19758722d2f3" />

#### 3. JSPolygon 편집 API 추가
  * 이동, 회전, 스케일
  * [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)
```javascript
let polygon = Module.createPolygon("POLYGON");

// 이동
polygon.move(longitude, latitude, alttitude);

// 회전
polygon.setRotation(x, y, z);

// 스케일
polygon.setScale(x, y, z);
```

#### 4. JSObject3D 축의 끝점 좌표 반환 API 추가
  * 회전, 스케일 시 축을 생성하여 직관적으로 확인할 수 있도록 축의 끝점 좌표를 반환하는 API가 추가되었습니다.
  * 중심과 끝점으로 라인을 생성합니다.
  * [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)
```javascript
// axis (x: 0, y: 1, z: 2)
let endpoint = getAxisEndpoint(axis, length);
```
#### 5. 카메라 이동 오류 수정 [(이슈 #514)](https://github.com/EgisCorp/XDWorld/issues/514)
 - 카메라 이동 후 간헐적으로 카메라 방향이 틀어지는 현상이 있어 수정되었습니다.
#### 6. 심플모드 건물에서 Hsv 옵션 [(이슈 #512)](https://github.com/EgisCorp/XDWorld/issues/512)
  * 건물 레이어가 심플모드인 경우에도 Hsv 옵션이 정상 동작하도록 수정되었습니다.

#### 7. 타일 레이어의 폴리곤 기반 요청 영역 지정
  * JSLayer의 setLimitBoundary API가 기존 사각 영역을 포함하여 폴리곤 영역도 수용하도록 변경되었습니다.
  * 건물의 중점이 폴리곤 영역에 포함되면 데이터를 로드합니다.
  * createXDServerLayer API에 boundaryLimit 옵션으로도 설정할 수 있습니다.
    ``` javascript
    Module.getTileLayerList().createXDServerLayer({
	  url : "https://xdworld.server.url",
	  servername : "XDServer",
	  name : "layer_name",
	  type : 9,
	  minLevel : 0,
	  maxLevel : 15,
	  boundaryLimit : [
		[126.93005255915998, 37.529214172573376, 0.0],
		[126.94102835336719, 37.52029412432422, 0.0],
		[126.93891529125652, 37.51798498831805, 0.0],
		[126.92841620055285, 37.516978366894115, 0.0],
		[126.92514862234246, 37.51770012779483, 0.0],
		[126.91756299430655, 37.521708873949606, 0.0],
	  ]
    });
    ```

#### 8. 지형 이미지 음영 마스킹 기능 추가
  * 경위도 최소, 최대 좌표로 지정한 영역 외 지형 이미지를 음영처리하는 옵션 API가 추가되었습니다. 
    ``` javascript
    Module.getTerrain().setImageMask({
        active : true,
        range : {
            min : [126.917562, 37.516978],
            max : [126.941028, 37.529214],
        },
        color : {a : 200, r : 0, g : 0, b : 0}
    });
    ```

#### 9. 지형 내장 이미지 사용 여부 설정 API 추가
  * 엔진 내 내장된 0레벨 지구본 이미지 사용 여부를 설정하는 옵션이 Module.initialize API에 추가되었습니다.
  * true로 설정하는 경우 내장된 이미지를 사용하며, false로 설정하는 경우 지정한 이미지 서버로 0레벨 이미지를 요청합니다.
  * 디폴트 값은 true 입니다.
    ``` javascript
    Module.initialize({
        container: document.getElementById("map"),
        terrain : {
            dem : {
                url : "...",
                name : "dem",
                servername : "XDServer",
            },
            image : {
                url : "...",
                name : "tile",
                servername : "XDServer",
                useBuiltInZeroImage : false    // false로 설정 시 지정한 서버로부터 0레벨 이미지 수신
            },						
        },
        ....
    }
    ```

### 2.19.0 (2025/10/13)
#### 1. Overlay Function Bug Fix [(Issue #513)](https://github.com/EgisCorp/XDWorld/issues/513)

* Fixed an issue where a black image was occasionally overlaid.
* Added an option for overlay image transparency.

```javascript
polygon.setOverlayObject({
	style : "polygon",
	coordinate : vertex,
	alpha : 0.6,           // newly added option
	image : _image
});
```

* Fixed an issue where overlays were not applied in building simple mode.
  If you don’t want to render building outlines:
  `Module.SetSimpleModeLineRender(false);`
<img width="969" height="690" alt="image" src="https://github.com/user-attachments/assets/1698f5ff-6e9a-41a4-9379-ffc96a83951a" />

#### 2. Improved Line Object GLOW Effect

* The existing GLOW effect has been enhanced.
<img width="645" height="619" alt="image" src="https://github.com/user-attachments/assets/c332909c-dd91-4c26-8dd4-c3cb1a3aa26c" />

#### 3. Added JSPolygon Editing API

* Supports move, rotate, and scale operations.
* [Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)

```javascript
let polygon = Module.createPolygon("POLYGON");

// Move
polygon.move(longitude, latitude, altitude);

// Rotate
polygon.setRotation(x, y, z);

// Scale
polygon.setScale(x, y, z);
```

#### 4. Added API for Returning JSObject3D Axis Endpoints

* Added an API that returns the endpoints of axes for visual confirmation during rotation and scaling.
* You can create lines between the center and each endpoint.
* [Sandbox Sample](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_edit)

```javascript
// axis (x: 0, y: 1, z: 2)
let endpoint = getAxisEndpoint(axis, length);
```

#### 5. Camera Movement Bug Fix [(Issue #514)](https://github.com/EgisCorp/XDWorld/issues/514)

* Fixed an issue where the camera direction was occasionally misaligned after movement.

#### 6. HSV Option in Simple Mode Buildings [(Issue #512)](https://github.com/EgisCorp/XDWorld/issues/512)

* Fixed an issue where the HSV option did not function properly when the building layer was in simple mode.

#### 7. Polygon-Based Request Area for Tile Layers

* The `setLimitBoundary` API of `JSLayer` now supports polygon areas in addition to rectangular ones.
* Building data is loaded when the building’s center point is within the polygon area.
* You can also configure this using the `boundaryLimit` option in the `createXDServerLayer` API.

```javascript
Module.getTileLayerList().createXDServerLayer({
	url : "https://xdworld.server.url",
	servername : "XDServer",
	name : "layer_name",
	type : 9,
	minLevel : 0,
	maxLevel : 15,
	boundaryLimit : [
		[126.93005255915998, 37.529214172573376, 0.0],
		[126.94102835336719, 37.52029412432422, 0.0],
		[126.93891529125652, 37.51798498831805, 0.0],
		[126.92841620055285, 37.516978366894115, 0.0],
		[126.92514862234246, 37.51770012779483, 0.0],
		[126.91756299430655, 37.521708873949606, 0.0],
	]
});
```

#### 8. Added Terrain Image Shading Mask Feature

* Added an API option to shade areas of the terrain image outside a specified coordinate range.

```javascript
Module.getTerrain().setImageMask({
	active : true,
	range : {
		min : [126.917562, 37.516978],
		max : [126.941028, 37.529214],
	},
	color : {a : 200, r : 0, g : 0, b : 0}
});
```

#### 9. Added Option to Enable/Disable Built-In Terrain Base Image

* Added a new option in `Module.initialize` to enable or disable the engine’s built-in level 0 globe image.
* When set to `true`, the built-in image is used; when set to `false`, the level 0 image is requested from the specified image server.
* Default value: `true`.

```javascript
Module.initialize({
	container: document.getElementById("map"),
	terrain : {
		dem : {
			url : "...",
			name : "dem",
			servername : "XDServer",
		},
		image : {
			url : "...",
			name : "tile",
			servername : "XDServer",
			useBuiltInZeroImage : false    // When false, fetch level 0 image from the specified server
		},						
	},
	....
});
```

---

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
