[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual
### Demos & Sandbox - https://sandbox.egiscloud.com
### Demos & Sandbox (beta) : https://sandbox.egiscloud.com/code/main.do?id=start&engine=beta&worker=true

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

### 1.60.0 / beta 2.2.0 (2024/3/29)

#### 1. 건물을 통과하여 직선거리를 분석하는 API 추가
  * 시작점과 끝점의 높이/거리/(오브젝트를 통과하여)직선거리를 측정하는 <측량> 기능이 추가되었습니다.
  * `JSOption`에 해당 기능의 콜백 함수를 등록할 수 있는 `callBackAltDistance()` API가 추가되었습니다. 
    * [샌드박스 링크](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_altdistance)
  * 마우스 모드에 `MML_ANALYS_ALTDISTANCE`가 추가되었습니다.

### 1.60.0 / beta 2.2.0 (2024/3/29)

#### 1. Added API for analyzing straight-line distance passing through buildings
  * The <Measurement> feature has been added to measure the height/distance/straight distance(passing through objects) between the starting point and the ending point.
  * Added `callBackAltDistance()` API to `JSOption` for registering callback functions for this feature.
    * [sandbox link](https://sandbox.egiscloud.com/code/main.do?id=analysis_measure_altdistance)
  * Added MML_ANALYS_ALTDISTANCE to mouse modes.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
