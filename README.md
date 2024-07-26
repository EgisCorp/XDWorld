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

### 2.5.0 (2024/7/26)

#### 1. 웹 워커 기능 개선
  * 기능 개선 및 파일 용량을 감소하여 기능 개선하였습니다.
#### 2. 도로 시설물 생성 기능 개선
  * 도로 시설물 중 교량의 교각이 일정 높이 이하인 부분은 생성이 되지 않도록 예외처리 단계가 추가되었습니다.
#### 3. 빌보드 수직선 옵션 추가
  * 빌보드 중심을 기준으로, 지면까지의 수직선을 생성 및 수정하는 API가 추가되었습니다.
    ``` javascript
	parameter = {
		visible: true,						// 가시화 여부(기본값: false)
		width: 10.0,						// 수직선 두께(기본값: 1.0)
		color: JSColor(255, 15, 100, 200),	// 수직선 색상(기본값: JSColor(255, 255, 255, 255))
		altitude: 30.0						// 수직선 끝점 고도(기본값: 0)
	}
	billboard.setVerticalLine(parameter);
    ```
  * 성공적으로 생성/수정하였을 경우 true를 반환합니다.
  * API의 자세한 사용법은 샌드박스 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_line)를 확인해주시기 바랍니다.
#### 4. 지형의 0레벨 지구본 위성영상 자체 포함
  * 0레벨에 대한 지구본 위성영상을 자체 포함하도록 적용 되었습니다.
  * 지도 서버에 연결이 정상적이 않아도 지구본은 기본적으로 구성됩니다.
  * 0 레벨 요청을 실패하여 반복적 네트워크 요청을 처리하지 않습니다.
  * 엔진의 파일용량이 소폭 증가합니다.

### 2.5.0 (2024/7/26)

#### 1. Improved Web Worker Functionality
  * Enhanced functionality and reduced file size to improve performance.
  
#### 2. Improved Road Facility Generation
  * Added an exception handling step to ensure that bridge piers below a certain height are not generated in road facilities.
  
#### 3. Added Vertical Line Option for Billboards
  * Added an API to create and modify vertical lines from the center of a billboard to the ground.
    ```javascript
	parameter = {
		visible: true,						// Visibility (default: false)
		width: 10.0,						// Line width (default: 1.0)
		color: JSColor(255, 15, 100, 200),	// Line color (default: JSColor(255, 255, 255, 255))
		altitude: 30.0						// Line end altitude (default: 0)
	}
	billboard.setVerticalLine(parameter);
    ```
  * Returns true if the vertical line is successfully created or modified.
  * For detailed usage of the API, please refer to the sandbox [link](https://sandbox.egiscloud.com/code/main.do?id=object_billboard_line).

#### 4. Integrated Zero-Level Globe Satellite Imagery for Terrain
  * Applied zero-level globe satellite imagery to be self-contained.
  * The globe is rendered by default even if the connection to the map server is not functioning properly.
  * Repeated network requests for failed zero-level requests are not processed.
  * The engine file size increases slightly.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
