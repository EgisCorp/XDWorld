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
### 2.17.1 (2025/08/21)
### 1. 이미지 기반 오버레이 기능 구현 [(이슈 502)](https://github.com/EgisCorp/XDWorld/issues/502)
  * 기존 색상으로만 표현되던 오버레이 기능을 이미지 기반으로도 적용할 수 있도록 기능이 업데이트 되었습니다.
    ``` javascript
    var polygon = Module.createOverlayObject("POLYGON");		
    var color = new Module.JSColor(255, 255, 0);		
    polygon.setOverlayObject({
  	  style : "polygon",
  	  coordinate : vertex,
	  color : color,
	  image : {
		width : img.width,
		height : img.height,
		data : ctx.getImageData(0, 0, img.width, img.height).data,
	  }
    });
    ```

### 2. 수인한도분석 결과값 추가
  * 각 격자에 시간대별 일조량 추가
    ```javascript
    [결과값]
    0 : {
    	analysisList: {
    		0 : {sunrise: true, time: 10},	// sunrise(일조인지 아닌지), time(일조 시간, 입력한 분석텀)
    		1 : {sunrise: true, time: 10},
    		.
    		.
    		.
    	}, 
    	color: {
    		A : 120,
    		R : 166,
    		G : 166,
    		B : 166
    	}, 
    	continuevalue: 50, 
    	id: 'grid_0', 
    	isanalysis: true,
    	position : {
    		alt: 3.981043982319534,
    		lat: 35.1712107372302,
    		lon: 129.13061351968938
    	},
    	totalvalue : 500
    }
    .
    .
    .
    ```

### 3. 하드웨어 가속 옵션 삭제
  * 하드웨어 가속 옵션 UI 삭제 및 console 경고 안내

### 4. AABB 추가
  * ECEF 좌표계에서의 AABB 좌표를 반환하는 기능이 추가되었습니다.
    ``` javascript
    var box = _polygon.getBoundary();
    // AABB Coordinates to Spherical Coordinates
    // bottom(4), top(4)
    var boxArray = box.getBox();
    
    const corners = {
    	bottom: [
    		[boxArray.get(0).longitude, boxArray.get(0).latitude, boxArray.get(0).altitude],
    		[boxArray.get(1).longitude, boxArray.get(1).latitude, boxArray.get(1).altitude],
    		[boxArray.get(2).longitude, boxArray.get(2).latitude, boxArray.get(2).altitude],
    		[boxArray.get(3).longitude, boxArray.get(3).latitude, boxArray.get(3).altitude],
    	],
    	top: [
    		[boxArray.get(4).longitude, boxArray.get(4).latitude, boxArray.get(4).altitude],
    		[boxArray.get(5).longitude, boxArray.get(5).latitude, boxArray.get(5).altitude],
    		[boxArray.get(6).longitude, boxArray.get(6).latitude, boxArray.get(6).altitude],
    		[boxArray.get(7).longitude, boxArray.get(7).latitude, boxArray.get(7).altitude],
    	]
    };
    ```

### 2.17.0 (2025/08/11)
### 1. Figure 객체 편집 UI 제어 API 추가
  - scaleLock, rotateLock, moveLock
    ```javascript
    let fig = Module.createFigure("figs");
    
    // 크기 UI 삭제
    fig.scaleUI = false;
    
    // 회전 UI 삭제
    fig.rotateUI = false;
    
    // 이동 UI 삭제
    fig.moveUI = false;
    ```

### 2. 하드웨어 가속 옵션 안내
  - Chrome 브라우저가 아닐 경우 Chrome 브라우저 권장 안내
    
    <img width="436" height="124" alt="image" src="https://github.com/user-attachments/assets/4f0f740c-4d97-44c1-a4f3-e8f9b00bbf2b" />


  - Chrome 브라우저의 "하드웨어 가속" or "그래픽 가속" 을 사용하지 않을 경우 안내
    
    <img width="497" height="283" alt="image" src="https://github.com/user-attachments/assets/56b44112-ee37-4ae9-b722-0164d397ed14" />


### 3. Indicator 기능 개선
 * 타겟이 카메라 뒤에 있는 경우 Indicator가 정상적으로 계산되지 않는 현상을 수정하였습니다.

### 2.17.1 (2025/08/21)
### 1. Image-Based Overlay Feature Implementation [(Issue 502)](https://github.com/EgisCorp/XDWorld/issues/502)

* The overlay feature, which previously only supported color-based rendering, has been updated to support image-based overlays as well.

  ```javascript
  var polygon = Module.createOverlayObject("POLYGON");		
  var color = new Module.JSColor(255, 255, 0);		
  polygon.setOverlayObject({
  	style : "polygon",
  	coordinate : vertex,
    color : color,
    image : {
      width : img.width,
      height : img.height,
      data : ctx.getImageData(0, 0, img.width, img.height).data,
    }
  });
  ```

### 2. Addition of Sunshine Duration Analysis Results

* Added time-based sunlight exposure data for each grid.

  ```javascript
  [Result]
  0 : {
  	analysisList: {
  		0 : {sunrise: true, time: 10},	// sunrise (whether it’s exposed to sunlight), time (sunlight duration, based on input interval)
  		1 : {sunrise: true, time: 10},
  		.
  		.
  		.
  	}, 
  	color: {
  		A : 120,
  		R : 166,
  		G : 166,
  		B : 166
  	}, 
  	continuevalue: 50, 
  	id: 'grid_0', 
  	isanalysis: true,
  	position : {
  		alt: 3.981043982319534,
  		lat: 35.1712107372302,
  		lon: 129.13061351968938
  	},
  	totalvalue : 500
  }
  .
  .
  .
  ```

### 3. Removal of Hardware Acceleration Option

* The hardware acceleration option UI has been removed, and a console warning is now provided instead.

### 4. Addition of AABB (Axis-Aligned Bounding Box)

* A new feature has been added to return AABB coordinates in the ECEF coordinate system.

  ```javascript
  var box = _polygon.getBoundary();
  // AABB Coordinates to Spherical Coordinates
  // bottom(4), top(4)
  var boxArray = box.getBox();

  const corners = {
  	bottom: [
  		[boxArray.get(0).longitude, boxArray.get(0).latitude, boxArray.get(0).altitude],
  		[boxArray.get(1).longitude, boxArray.get(1).latitude, boxArray.get(1).altitude],
  		[boxArray.get(2).longitude, boxArray.get(2).latitude, boxArray.get(2).altitude],
  		[boxArray.get(3).longitude, boxArray.get(3).latitude, boxArray.get(3).altitude],
  	],
  	top: [
  		[boxArray.get(4).longitude, boxArray.get(4).latitude, boxArray.get(4).altitude],
  		[boxArray.get(5).longitude, boxArray.get(5).latitude, boxArray.get(5).altitude],
  		[boxArray.get(6).longitude, boxArray.get(6).latitude, boxArray.get(6).altitude],
  		[boxArray.get(7).longitude, boxArray.get(7).latitude, boxArray.get(7).altitude],
  	]
  };
  ```

### 2.17.0 (2025/08/11)
### 1. Added API to control Figure object editing UI

* `scaleLock`, `rotateLock`, `moveLock`

  ```javascript
  let fig = Module.createFigure("figs");
  
  // Remove scale UI
  fig.scaleUI = false;
  
  // Remove rotation UI
  fig.rotateUI = false;
  
  // Remove movement UI
  fig.moveUI = false;
  ```

### 2. Hardware acceleration guidance

* If the browser is not Chrome, display a recommendation to use Chrome.

  <img width="436" height="124" alt="image" src="https://github.com/user-attachments/assets/4f0f740c-4d97-44c1-a4f3-e8f9b00bbf2b" />

* If Chrome's "Hardware Acceleration" or "Graphics Acceleration" is disabled, display a notice.

  <img width="497" height="283" alt="image" src="https://github.com/user-attachments/assets/56b44112-ee37-4ae9-b722-0164d397ed14" />

### 3. Indicator feature improvements

* Fixed an issue where the indicator was not calculated correctly when the target was behind the camera.

---




## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
