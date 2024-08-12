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

### 2.5.1 (2024/08/09)

#### 1. JSHTMLObject 이동 기능 추가
  * JSHTMLObject 내부 변수 "position"을 통해 현재 위치와, 변경 위치 설정하는 변수가 추가되었습니다.
    ``` javascript
    // Get
    let position = htmlObject.position;
    // Set
    let position = new Module.JSVector3D(lon, lat, alt);
    htmlObject.position = position;    
    ```
  * 입력, 출력은 경위도 값이 기준입니다.

#### 2. POI 가시범위 API 기능 개선 확장
  * JSPoint에 개선된 가시범위 설정 API가 추가되었습니다.
    ``` javascript
      // 가시 범위 설정 예시
      poi.setRange(
              {
                  enable : true,      // 가시 범위 사용 여부 setVisibleRange의 bEnable 파라메터와 동일
                  min : 1.0,          // 가시 범위 최소 범위 setVisibleRange의 dMin 파라메터와 동일
                  max : 1000.0,       // 가시 범위 최대 범위 setVisibleRange의 dMax 파라메터와 동일
                  textMin : 1.0,      // 가시 범위 텍스트 최소 범위 min 과 같거나 커야함
                  textMax : 300.0     // 가시 범위 텍스트 최대 범위 max 과 같거나 작아야함
              }
          );
    ```
  * 기존 POI 객체 표현범위 설정 (Icon 기준)에서 Text에 대한 추가 표현 범위를 설정합니다.

#### 3. JSPipe 흐름 화살표 기능 개선
  * 평면 형태의 화살표를 3차원 입체 구조로 개선하였습니다.
  * 일부 지역에서 화살표 생성 시 방향이 올바르게 정렬되지 않는 현상을 수정하였습니다.
  * 파이프 지점 높낮이에 따라 화살표의 틸트 각도가 함께 적용되도록 수정하였습니다.

#### 4. face 데이터로 JSPolygon을 생성하는 'JSPolygon.createWithFaces()' API 추가
  * 사용자가 정의한 face 데이터를 기반으로 JSPolygon을 생성하는 기능이 추가되었습니다.
  * 사용자는 형식에 맞춘 JSON 데이터를 파라메터로 전달함으로써, JSPolygon을 생성할 수 있습니다.
  * 자세한 사용법은 샌드박스 [링크](https://sandbox.egiscloud.com/code/main.do?id=object_faces_to_polygon)를 참고하시기 바랍니다.
  ``` javascript
let parameter = {
	upVector: /*업벡터 좌표축*/,
	cullMode: /*버텍스 정의 방향*/,
	position: /*모델 중심 위치*/,
	moveOffset: /*위치 오프셋(세부 조정)*/,
	faceInfo: [
		{
			vertex: /*버텍스 위치*/,
			matrix: /*변환(4x4 행렬)*/,
			indexVertex: /*버텍스 인덱스*/,
			indexUV: /*텍스처 좌표 인덱스*/,
			uv: /*실제 텍스처 좌표*/,
			normal: /*노멀 벡터*/,
			color: /*색상*/
		}
	]
}
polygon.createWithFaces(parameter);
  ```

### 2.5.1 (2024/08/09)

#### 1. Added JSHTMLObject Movement Feature
  * An internal variable "position" has been added to JSHTMLObject to set and get the current and new positions.
    ``` javascript
    // Get
    let position = htmlObject.position;
    // Set
    let position = new Module.JSVector3D(lon, lat, alt);
    htmlObject.position = position;    
    ```
  * Input and output are based on latitude and longitude values.

#### 2. Expanded POI Visibility Range API
  * An improved visibility range setting API has been added to JSPoint.
    ``` javascript
      // Example of setting visibility range
        poi.setRange(
                {
                    enable : true,      // Whether to use visibility range, same as bEnable parameter of setVisibleRange
                    min : 1.0,          // Minimum visibility range, same as dMin parameter of setVisibleRange
                    max : 1000.0,       // Maximum visibility range, same as dMax parameter of setVisibleRange
                    textMin : 1.0,      // Minimum text visibility range, must be equal to or greater than min
                    textMax : 300.0     // Maximum text visibility range, must be equal to or less than max
                }
            );
    ```
  * Adds additional visibility range settings for text in the existing POI object representation (Icon-based).

#### 3. Improved JSPipe Flow Arrow Feature
  * The flat arrow has been upgraded to a 3D structure.
  * Fixed an issue where arrows were not properly aligned in some areas.
  * Adjusted the arrow's tilt angle according to the elevation of pipe points.

#### 4. Added 'JSPolygon.createWithFaces()' API for Creating JSPolygon from Face Data
  * Added functionality to create a JSPolygon based on user-defined face data.
  * Users can generate a JSPolygon by providing JSON data in the correct format as a parameter.
  * For detailed usage, please refer to the [sandbox sample](https://sandbox.egiscloud.com/code/main.do?id=object_faces_to_polygon).
    ``` javascript
      let parameter = {
        upVector: /* Up vector coordinate axis */,
        cullMode: /* Vertex definition direction */,
        position: /* Model center position */,
        moveOffset: /* Position offset (fine adjustment) */,
        faceInfo: [
          {
            vertex: /* Vertex position */,
            matrix: /* Transformation (4x4 matrix) */,
            indexVertex: /* Vertex index */,
            indexUV: /* Texture coordinate index */,
            uv: /* Actual texture coordinates */,
            normal: /* Normal vector */,
            color: /* Color */
          }
        ]
      }
      polygon.createWithFaces(parameter);
    ```

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
