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

## Notice

### 비디오 텍스쳐 기능 개선
* 사용자 편의성을 위해 객체 생성 이후의 기능들 엔진 내부에 삽입 및 속도개선되었습니다.
* 기존 비디오 텍스쳐 관련 기능은 2024년까지 지원합니다.
* 새로운 사용법은 [비디오 텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture), [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

### Improvements to video texture function
* For user convenience, functions after object creation have been inserted into the engine and speed has been improved.
* Existing video texture-related features will be supported until 2024.
* New usage methods include [Video Texture](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture), [Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video), [led board](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT Video](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture).

## Update

### 2.9.2 (2024/12/16)

#### 1. `Real3D` 텍스처 요청 개수 제한 API 추가
  - `Real3D`에서 최대 텍스처 요청 개수를 제한할 수 있도록, `JSOption::setMaxRequestTextureQueueSize()` API가 추가되었습니다.

    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | maxTextureSize | number | <p>텍스처를 요청하는 최대 개수(1~20개).</p> |

    ```javascript
    Module.getOption().setMaxRequestTextureQueueSize(20); // 20개의 텍스쳐 요청
    ```

#### 2. `Real3D` 텍스처 레벨 고정 API 추가
  - `Real3D`에서 요청하는 텍스처 레벨을 고정할 수 있도록, `JSMap::fixedTextureLevel()` API가 추가되었습니다.

    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | level | number | <p>텍스처 요청하는 레벨(0~5).</p> |
    ``` javascript
    Module.getMap().fixedTextureLevel(0);   // 고정레벨 지정
    ``` 

### 2.9.1 (2024/12/06)

#### 1. glTF 모델의 회전 및 크기 조절 기능 추가
  * glTF 모델을 유연하게 사용할 수 있도록, 회전과 크기 조절 기능이 추가되었습니다.
  * 회전의 경우 XYZ축을 기준으로 회전 각도를 조절할 수 있습니다.
    ```javascript
    var polygon = Module.createGLTF("GLTF_Object");
      polygon.loadFile({
        url : url,
        type : "glb",
        position : pos,
        rotate : [ 0, 90, 0], // XYZ 축 방향 회적 각도(Degree)
                    scale : [ 1.0, 10.0, 1.0], // XYZ축 방향 스케일 변경. (1.0= 원래 크기)
        rebuild : true,
      });
    ```

#### 2. split view 하이브리드 가시화 기능 추가
  * 하이브리드 모드가 `split view`에서도 정상적으로 보일 수 있도록 기능을 추가하였습니다.

#### 3. stereo view/split view 모드 오브젝트 렌더링 오류 수정
  - `stereo view/split view` 모드에서, 반투명한 상태의 오브젝트 출력이 제대로 되지 않는 오류를 수정하였습니다.

#### 4. JSPolygon::setHeightByType() API 추가
  - `type`에 따라 평면 폴리곤의 윗면을 생성하는 API를 추가하였습니다.

    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | heightOrAltitude | number | <p>버텍스에 적용할 높이 혹은 고도.</p><p>0일 경우: 높이로 사용.</p><p>1일 경우: 고도로 사용.</p> |
    | type | number | <p>윗면 생성 방식 설정.</p><p>0일 경우: 각 밑면 버텍스에서 height만큼 높인 윗면 생성.</p><p>1일 경우: 균일한 고도의 평평한 윗면 생성.</p> |
    ```javascript
    var polygon = Module.createPolygon("POLYGON");
    var vertex = new Module.JSVec3Array();
    var part = new Module.Collection();

    for (var i = 0; i < _vertex.length; i++) {
      for (var j = 0; j < _vertex[i].length; j++) {
        vertex.push(_vertex[i][j]);
      }
      part.add(_vertex[i].length);
    }
    polygon.setPartCoordinates(vertex, part);

    // Set as a polyhedron polygon with height
    // type == 0
    //polygon.setHeightByType(80, 0);
    // type == 1
    polygon.setHeightByType(120, 1);

      //...
    ```

### 2.9.0 (2024/11/29)

#### 1. Inspector 기능 항목 추가
  * 기존 `Inspector` 기능에서, 지형 데이터(dem/image)를 요청하는 대기열의 크기를 확인할 수 있도록 수정하였습니다.
  * 자세한 사용법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=option_inspector)을 참고해주시기 바랍니다.

### 2.9.2 (2024/12/16)

#### 1. Added API to Limit the Number of Texture Requests in `Real3D`
  - `JSOption::setMaxRequestTextureQueueSize()` has been introduced to limit the maximum number of texture requests in `Real3D`.

    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | maxTextureSize | number | <p>The maximum number of texture requests (1–20).</p> |

    ```javascript
    Module.getOption().setMaxRequestTextureQueueSize(20); // Request up to 20 textures
    ```

#### 2. Added API to Fix Texture Level in `Real3D`
  - `JSMap::fixedTextureLevel()` has been introduced to fix the texture level requested in `Real3D`.

    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | level | number | <p>The texture level to request (0–5).</p> |
    ``` javascript
    Module.getMap().fixedTextureLevel(0);   // Set a fixed texture level
    ``` 

### 2.9.1 (2024/12/06)

#### 1. Added Rotation and Scaling Features for glTF Models
  * Rotation and scaling functionalities have been added to make glTF models more versatile.
  * For rotation, the angle can be adjusted based on the XYZ axes.
    ```javascript
    var polygon = Module.createGLTF("GLTF_Object");
      polygon.loadFile({
        url : url,
        type : "glb",
        position : pos,
        rotate : [ 0, 90, 0], // Rotation angles in degrees for the XYZ axes
                    scale : [ 1.0, 10.0, 1.0], // Scaling factors for the XYZ axes (1.0 = original size)
        rebuild : true,
      });
    ```

#### 2. Added Hybrid Visualization Functionality in Split View
  * A feature has been added to ensure hybrid mode is properly displayed in `split view`.

#### 3. Fixed Object Rendering Issues in Stereo View/Split View Modes
  - Fixed an issue where translucent objects were not rendered correctly in `stereo view` or `split view mode`.

#### 4. Added JSPolygon::setHeightByType() API
  - Introduced an API to generate the top face of a planar polygon based on the `type` parameter.
    | Name  | Type    | Description                               |
    | ----- | ------- | ----------------------------------------- |
    | heightOrAltitude | number | <p>The height or altitude to apply to vertices.</p><p>If 0: used as height.</p><p>If 1: used as altitude.</p> |
    | type | number | <p>Determines the method for creating the top face.</p><p>If 0: Top face is elevated based on individual vertex heights.</p><p>If 1: Creates a flat top face at uniform altitude.</p> |
    ```javascript
    var polygon = Module.createPolygon("POLYGON");
    var vertex = new Module.JSVec3Array();
    var part = new Module.Collection();

    for (var i = 0; i < _vertex.length; i++) {
      for (var j = 0; j < _vertex[i].length; j++) {
        vertex.push(_vertex[i][j]);
      }
      part.add(_vertex[i].length);
    }
    polygon.setPartCoordinates(vertex, part);

    // Set as a polyhedron polygon with height
    // type == 0
    //polygon.setHeightByType(80, 0);
    // type == 1
    polygon.setHeightByType(120, 1);

      //...
    ```

### 2.9.0 (2024/11/29)

#### 1. Added Inspector Feature
  * The existing Inspector feature has been updated to allow checking the size of the queue for terrain data (DEM/Image) requests.
  * For detailed instructions, please refer to [sample](https://sandbox.egiscloud.com/code/main.do?id=option_inspector).

#### Notice
  * There is currently an issue in [Viewshed(3D)](https://sandbox.egiscloud.com/code/main.do?id=analysis_viewshed_3d) where the polygon representing the viewshed is not displayed in the correct position. We will address this as soon as possible.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
