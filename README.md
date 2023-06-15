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

### 1.51.0 업데이트 (2023년 5월 26일)
#### 1. 화면 분할 환경에서 오브젝트의 렌더링 오류 수정 [Issue #289](/../../issues/289)
 * 화면 분할 시 투명도가 있는 오브젝트가 지정된 화면 구분 없이 렌더링 되는 현상을 수정하였습니다.

#### 2. 창문분석 기능 추가
 * 창문 영역(좌하단, 우상단 or 좌상단, 우하단)을 선택 후 창문 생성, 복사/붙여넣기, 층 복사하여 창문분석을 합니다.
 * 분석 결과는 json 형태로 반환되며, 연속 일조량, 전체 일조량이 반환됩니다.
 * [샌드박스(창문분석)](http://sandbox.dtwincloud.com/code/main.do?id=analysis_window_shadow)

### 1.51.1(Hotfix) 업데이트 (2023년 6월 2일)
#### 1. 컬러 폴리곤 생성 기능 추가
 * 다수의 정점(vertex)과 인덱싱 정보로 폴리곤 형상을 직접 정의할 수 있는 API가 추가되었습니다.
   * 정점(vertex) : 폴리곤을 구성하는 점의 위치 리스트
   * 인덱스 : 각 정점을 삼각형으로 매핑하는 정수 리스트 

  ![image](https://github.com/avamk2/XDWorld_WebGL/assets/82925313/15f83298-2bd8-456a-9058-372809185519)

* 각 정점은 1:1로 매칭되는 색상 리스트를 정의할 수도 있습니다. 

  ![image](https://github.com/avamk2/XDWorld_WebGL/assets/82925313/9ff23a9d-7689-4f10-860e-7d0a00e3b93d)

* 버텍스만으로 폴리곤의 삼각형을 구성하는 경우 인덱스를 생략할 수도 있습니다. 단, 이 경우 중복된 점이 리스트에 추가되므로 인덱싱 방법보다 비효율적일 수 있습니다. 

  ![image](https://github.com/avamk2/XDWorld_WebGL/assets/82925313/0e6c3f1c-0de5-47c9-b4b4-570841913807)

* 해당 기능은 JSColorPolygon의 set API를 통해 활용하실 수 있습니다.
   ``` javascript
   var polygon = Module.createColorPolygon("GRADATION_POLYGON");
   polygon.set({
       vertex : [
           new Module.JSVector3D(129.12909050967076, 35.17110889362373, 4.22),
           new Module.JSVector3D(129.130474460754, 35.17110084682464, 4.00),
           new Module.JSVector3D(129.13056137846394, 35.17032570132414, 4.07),
           new Module.JSVector3D(129.12921614563658, 35.17031032880493, 4.39)
       ],
       color : [
           new Module.JSColor("#FF0000"),
           new Module.JSColor("#FF0000"),
           new Module.JSColor("#FFFF00"),
           new Module.JSColor("#FFFF00")
       ],
       index : [0, 1, 2, 0, 2, 3]
   });
   ```
 * [샌드박스](https://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_color_gradation)에서 기능의 동작을 확인하실 수 있습니다.

#### 2. 라인 생성 시 각 지점 별 색상 설정 기능 추가
 * JSLineString으로 라인을 생성하였을 경우, 각 정점에 색상을 개별 지정 가능하도록 기능이 추가되었습니다.
 * 기존 API에서는 color 태그를 통해 단일 색상 지정만 가능했으나, 이번 업데이트를 통해 각 정점 별 색상 지정이 가능하도록 업데이트되었습니다.
 * 각 정점 별 색상 지정 시 color 태그에 색상값 배열을 입력하시면 됩니다.
 * 각 정점 별 색상 수가 1:1로 매칭되어야 합니다. 매칭되지 않을 시 배열의 첫번째 색상만 참조하여 단일 색상으로 적용됩니다.
   ``` javascript
   var line = Module.createLineString("GRADATION_LINE");
   line.createbyJson({
		coordinates: {
                    style : "XYZ",
                    coordinate : [
                        [129.12486405043842, 35.17410008274932, 5.7],
                        [129.12522538156702, 35.17364593649981, 5.6],
                        [129.12563286539853, 35.17332821268188, 5.6]
                    ]
                },
		type: 0,
		color: [
                    {a: 255, r : 255, g : 0, b : 
                    {a: 255, r : 255, g : 127, b : 0},
                    {a: 255, r : 255, g : 255, b : 0},
                ],
		width: 10.0
	});
   ```
 * [샌드박스](https://sandbox.dtwincloud.com/code/main.do?id=object_colorpolygon_color_gradation)에서 기능의 동작을 확인하실 수 있습니다.

### 1.51.2(Hotfix) 업데이트 (2023년 6월 9일)
#### 1. JSSolarManager API 업데이트
 * 태양광 패널 배치 정보 반환 API(getLayerPannelInfo)를 추가하였습니다.
 * 태양광 패널 직접 배치 가능 API(addPlannelObject)를 추가 하였습니다.
#### 2. [이슈 296](https://github.com/EgisCorp/XDWorld/issues/296#:~:text=%ED%99%94%EB%A9%B4%20%EC%98%A4%EB%A5%98%20%EB%AC%B8%EC%9D%98-,%23296,-Open) 오류 수정 완료

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
