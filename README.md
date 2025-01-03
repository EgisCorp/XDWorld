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
