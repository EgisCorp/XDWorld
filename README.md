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

### 1.59.1 (2024/3/8)

#### 1. createShadow API 실행 시 마우스 모드 고정 현상 수정 
  * JSAnlysis의 createShadow API 실행 시 마우스 모드가 일반 모드(1번)으로 고정되는 현상을 수정하였습니다. 

#### 2. JSFlowPolygon의 setHeight API 설정 오류 수정
  * setHeight API 설정 값에 오차가 발생하는 현상을 수정하였습니다.

#### 3. ETLT_TILE_LOD_MODEL 레이어의 LOD Max값 관련 함수 추가
  * JSLayer 클래스에 ETLT_TILE_LOD_MODEL 타입 레이어의 LOD Max 값을 설정/반환 하는 API가 추가되었습니다.
  * setTileLODMaxLevel(_nMaxLevel) : LOAD Max 값을 설정합니다(`-1`일 경우, 제한 없음). 기본값은 `-1`입니다.
  * getTileLODMaxLevel() : LOAD Max 값을 반환합니다.
    ``` javascript
    var layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("bldg_us_jsp");
    layer.setTileLODMaxLevel(3);
    ```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
