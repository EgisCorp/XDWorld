[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual
### Demos & Sandbox - https://sandbox.egiscloud.com
### Demos & Sandbox (beta) : https://sandbox.egiscloud.com/code/main.do?id=start&engine=beta&worker=true

# Introduction

> WebGL 기반 3D GIS 엔진 XDWORLD ENGINE

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## 특징

-   웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
-   멀티 OS, 브라우저, No-Plugin 지원
-   3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
-   거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
-   다양한 도시계획 시뮬레이션 및 분석 기능 제공
-   공간정보 오픈플랫폼(V World) 데이터 서비스 가능

## 적용분야

-   GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등

## 최근 업데이트

### 1.59.1 (2024/3/08)

#### 1. createShadow API 실행 시 마우스 모드 고정 현상 수정 
  * JSAnlysis의 createShadow API 실행 시 마우스 모드가 일반 모드(1번)으로 고정되는 현상을 수정하였습니다. 

#### 2. JSFlowPolygon의 setHeight API 설정 오류 수정
  * setHeight API 설정 값에 오차가 발생하는 현상을 수정하였습니다.

#### 3. ETLT_TILE_LOD_MODEL 타입의 레이어 LOD Max값 설정 API
* JSLayer 클래스
* setTileLODMaxLevel(_nMaxLevel) : LOAD Max 값 설정. -1이면 제한 없음. Default : -1
* getTileLODMaxLevel() : LOAD Max 값 리턴
``` javascript
var layerList = new Module.JSLayerList(false);
var layer = layerList.nameAtLayer("bldg_us_jsp");
layer.setTileLODMaxLevel(3);
```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
