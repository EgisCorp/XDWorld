[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/

### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual

### Demos & Sandbox - http://sandbox.dtwincloud.com

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

### 1.52.0 (2023/6/30)

#### 1. 레이어의 지상/지하 렌더링 구분 프로퍼티 추가 ([이슈 297](https://github.com/EgisCorp/XDWorld/issues/297))
 * 해당 레이어의 지상에 위치하는지, 혹은 지하에 위치하는지 구분하는 view_underground 프로퍼티가 추가되었습니다.
 * ``` layer.view_underground = true ```
 * 디폴트 값은 false 입니다. (Module.TILE_LAYER_TYPE_VECTOR_PIPE 타입 레이어에 한하여 디폴트 값은 true로 적용됩니다.)

#### 2. 태양광 패널관련 JSSolarManager API 업데이트
 * 태양광 패널에 배치 정보를 API 레벨로 받을 수 있는 getLayerPannelInfo 추가됩니다. 
    * 패널의 위치, 가로너비, 세로너비, 패널 두께, 방향각, 수직각 정보가 String Json 정보로 제공하며 아래 API로 재배치 가능합니다. 
 * 태양광 패널 정보를 바탕으로 직접 패널 배치하는 bool addPlannelObject 추가됩니다. 
* 옥상 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis_pannel_roof
* 지상 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis_pannel_terrain
* 배란다 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis_pannel_veranda
* 벽면(BI) 패널 배치 시뮬레이션 : http://sandbox.dtwincloud.com/code/main.do?id=analysis_pannel_wall

#### 3. JSVector3Array - JSVector2Array 간 변환 API 추가
 * JSVector3Array - JSVector2Array 간 원활한 변환이 가능하도록 toJSVector3Array, toJSVector2Array API가 추가되었습니다.
 * JSVector2Array에서 JSVector3Array로 변환하는 경우 고도 값 입력이 필요합니다.
 * JSVector3Array에서 JSVector2Array로 변환하는 경우 고도 값은 소실됩니다.
    ``` javascript
    var array2D = new Module.JSVector2Array();
    var array3D = new Module.JSVector3Array();
    ...
    console.log(array2D.toJSVector3Array(10.0));         // JSVector2Array에서 JSVector3Array로 변환
    console.log(array3D.toJSVector2Array());   // JSVector3Array에서 JSVector2Array로 변환
    ```

#### 4. JSVector3Array, JSVector2Array에 getBoundary API 추가
 * JSVector3Array, JSVector2Array의 min, max 값이 반환 되는 getBoundary API가 각각 추가되었습니다. 
    ``` javascript
    var boundary = array2D.getBoundary());
    console.log(boundary.min);
    console.log(boundary.max);
    ```
 * 리스트에 값이 없어 비어있는 경우 null을 반환합니다.

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
