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

### 2.10.2 (2025/01/21)

1. `3DTiles` 포맷 처리 기능 안정화
   - `3DTiles` 파일 처리 속도를 개선하였습니다.
   - 로딩한 모델이 깜박이는 오류를 수정하였습니다.

2. 성절토 바닥 타일링 텍스처 설정 API 추가
   - 성절토 바닥 텍스쳐 설정 시 텍스쳐 반복 출력(타일링)이 가능하도록 API가 추가되었습니다.
   - API 설정 시 1.0보다 큰 값을 n값을 입력하면 설정한 텍스쳐가 n번 반복 출력됩니다.
   - API 호출 이후 생성되는 성절토 객체에 해당 값이 적용됩니다.
   - bool setBottomTextureTilingScale(float u, float v)
     - class : JSEditTerrain
     - parameter
      - u : 가로 반복 u 좌표
      - v : 세로 반복 v 좌표
    ```javascript
      Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
    ```

3. `JSPolygon` 텍스처 오류 수정
   - `JSpolygon` 객체에 반투명한 텍스처가 제대로 적용되지 않는 오류를 수정하였습니다.

### 2.10.1 (2025/01/03)

1. `createTMCoordPlane()` 기능 개선
   - `createTMCoordPlane()` API의 매개변수 정의 방식이 수정되었습니다. 자세한 사항은 아래 문서를 확인하여 주시기 바랍니다.
     - 변경된 양식
        ```Javascript
        JSPolygon.createTMCoordPlane({
            llcorner : {
              coordCode : [좌표계코드, 필수],
              x : [좌하단 X 좌표, 필수],
              y : [좌하단 Y 좌표, 필수]
            },
            grid : {
              col : [그리드 가로 총수, 필수],
              row : [그리드 세로 총수, 필수],
              cellSize : [그리드 셀의 가로 세로 크기, 필수],
              ratioMode : [New 배율모드 사용 여부 0 - 기존 gab방식, 1 - 배율모드사용, 선택],
              xSplit : [ New 가로 분할 배율, ratioMode  1일때 필수],
              ySplit : [ New 세로 분할 배율, ratioMode  1일때 필수]
            }
          });
        ```
     - 사용 예시
        ```Javascript
        polygon.createTMCoordPlane({
          llcorner : {
            coordCode : 20,
            x : 216701.99445382116 ,
            y : 220328.8122727003
          },
          grid : {
            col : 644,
            row : 585,
            cellSize : 10,
            ratioMode : 1,
            xSplit : 10,
            ySplit : 10
          }
        });
        ```

### 2.10.0 (2024/12/27)

#### 1. `Stereo View` 모드의 로컬 레이어 오류 수정
  * `Stereo View` 모드에서 로컬 레이어를 사용할 경우, POI가 왼쪽 화면에만 그려지는 오류를 수정하였습니다.

### 2.10.2 (2025/01/21)

1. Stabilization of `3DTiles` Format Processing
   - Improved the processing speed for `3DTiles` files.
   - Fixed an issue where loaded models would flicker.

2. Added API for Tiling Texture Configuration on Seongjeolto Ground
   - An API has been added to enable texture tiling (repeated output) for the Seongjeolto ground texture configuration.
   - When specifying a value \(n > 1.0\), the texture will be repeated \(n\) times.
   - The specified value will apply to Seongjeolto objects created after the API call.
   - **bool setBottomTextureTilingScale(float u, float v)**
     - **Class**: JSEditTerrain
     - **Parameters**:
       - **u**: Horizontal tiling scale (u-coordinate)
       - **v**: Vertical tiling scale (v-coordinate)
     ```javascript
     Module.getEditTerrain().setBottomTextureTilingScale(10.0, 10.0);
     ```

3. Fixed Texture Issue with `JSPolygon`
   - Resolved an issue where semi-transparent textures were not properly applied to `JSPolygon` objects.

### 2.10.1 (2025/01/03)

1. Improvement to `createTMCoordPlane()` function

   - The parameter definition method for the `createTMCoordPlane()` API has been revised. Please refer to the document below for detailed information.

     - Updated format

       ```Javascript
       JSPolygon.createTMCoordPlane({
           llcorner : {
             coordCode : [Coordinate system code, required],
             x : [Lower-left X coordinate, required],
             y : [Lower-left Y coordinate, required]
           },
           grid : {
             col : [Total number of grid columns, required],
             row : [Total number of grid rows, required],
             cellSize : [Width and height of grid cells, required],
             ratioMode : [Use of new scale mode, 0 - Existing gap method, 1 - Use scale mode, optional],
             xSplit : [New horizontal split ratio, required if ratioMode is 1],
             ySplit : [New vertical split ratio, required if ratioMode is 1]
           }
         });
       ```

     - Example usage

       ```Javascript
       polygon.createTMCoordPlane({
         llcorner : {
           coordCode : 20,
           x : 216701.99445382116 ,
           y : 220328.8122727003
         },
         grid : {
           col : 644,
           row : 585,
           cellSize : 10,
           ratioMode : 1,
           xSplit : 10,
           ySplit : 10
         }
       });
       ```

### 2.10.0 (2024/12/27)

#### 1. Fixed Local Layer Error in `Stereo View` Mode
  * Resolved an issue in `Stereo View` mode where POIs (Points of Interest) were displayed only on the left screen when using local layers.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
