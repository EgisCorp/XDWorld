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

## Important note

- 1인칭 카메라 비디오 텍스쳐 기능 지원 중단
  * 기존 [1인칭 카메라 비디오 텍스쳐](https://sandbox.egiscloud.com/code/main.do?id=camera_video_texture)  기능은 2025년까지 지원합니다. 
  * JSCamera 클래스의 삭제 API ---------> JSVideoObject 클래스의 대체 API 
  - [x] setVideoInfo ---------> createVideo
  - [x] clearVideo -----------> clearTexture
  * JSCamera 클래스의 삭제 property ---------> JSVideoObject 클래스의 대체 property
  - [x] videoStreaming ---------------> videoStreaming
  - [x] videoFar -----------------------> far
  - [x] videoFovX ---------------------> fovX
  - [x] videoFovY ---------------------> fovY
  - [x] videoAlpha --------------------> alpha
  - [x] videoAxisX --------------------> axisX
  - [x] videoAxisY --------------------> axisY
  - [x] videoZoom --------------------> zoom
  - [x] videoFarPlane -----------------> background
  - [x] videoResolution ---------------> resolution
  - [x] videoObjectMapping ---------> objectMapping
  - [x] videoIsplayer ------------------> isPlayer
  * 비디오 객체  [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

## Update

- 다음 배포 일정: **2025년 4월 07일(월)**
- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.

### 2.12.0 (2025/03/10)

1. POI 선택시 Text 위치 오류 수정
    - POI 선택시 setTextMargin 이 Text 에 적용되지 않는 오류를 수정하였습니다.

2. 화면분할(Streo View) 모드에서 좌우 객체를 인식할 수 있도록 기능을 수정하였습니다.

3. Text 형태의 POI 선택 인식 및 선택 효과 추가
    - 기존 POI처럼 Text도 선택과 선택 색상(picking color) 적용이 가능하도록 수정하였습니다.

4. 3DTiles B3DM 선택 오류를 수정하였습니다.

5. `AutoMove` 모드에서 카메라 회전 옵션 `lock orientation` 추가
    - `AutoMove` 모드에서 카메라를 자유롭게 회전시킬 수 있도록, `lock orientation` 옵션이 추가되었습니다.
       - 활성화(기본값): 카메라가 항상 다음 경로의 위치를 바라봅니다.
       - 비활성화: 카메라를 1인칭 시점에서 회전시킬 수 있습니다(오른쪽 마우스 버튼 사용).
    - 사용 방법
        ```Javascript
        // AutoMove 설정
        Module.getViewCamera().setAnimationSpeed(1);
        Module.getViewCamera().startAutoMove();
        Module.XDRenderData();

        // 비활성화 함으로써, 카메라 자유롭게 이동 가능
        Module.getViewCamera().setLockOrientationAutoMove(false);
        ```
      - 자세한 사용 방법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path_visualize)을 확인해주시기 바랍니다.

6. 서비스 레이어 범위 제한 옵션 `boundaryLimit` 추가
     - 서비스 레이어에서 오브젝트를 요청할 때, 요청하는 범위를 경도/위도로 제한할 수 있도록 `boundaryLimit` 옵션이 추가되었습니다.
       - 활성화: 기존 방식에서, 미리 지정해 놓은 범위에 포함되는 오브젝트만 호출합니다.
          - 활성화한 이후에도, `JSLayer::setLimitBoundary()` API를 사용하여 범위를 제한하여야 합니다.
       - 비활성화(기본값): 기존 방식과 동일하게 오브젝트를 호출합니다.
     - 사용 방법
        ```Javascript
          // 샌드박스에서 제공하는 
          let layer = Module.getTileLayerList().createXDServerLayer({
            url : "https://xdworld.vworld.kr",
            servername : "XDServer3d",
            name : "facility_build",
            type : 9,
            minLevel : 0,
            maxLevel : 15
          });

          // Json 형태의 매개변수로 범위 지정
          layer.setLimitBoundary({
            boundary: {
              min: [129.125, 35.161],		// Lower left
              max: [129.141, 35.168]		// Upper right
            }
          });

          layer.boundaryLimit = true;   // 옵션 활성화
        ```
       - 자세한 사용 방법은 [샌드박스 샘플](https://sandbox.egiscloud.com/code/main.do?id=layer_request_boundary)을 확인해주시기 바랍니다.

### 2.12.0 (2025/03/10)

1. **Fixed Text Position Error When Selecting POI**  
   - Fixed an issue where `setTextMargin` was not applied to Text when selecting a POI.

2. **Improved Stereo View Mode to Recognize Left and Right Objects**  
   - Modified functionality to enable recognition of left and right objects in split-screen (Stereo View) mode.

3. **Added POI Selection Recognition and Effects for Text**  
   - Modified Text elements to allow selection and picking color application, similar to standard POIs.

4. **Fixed 3DTiles B3DM Selection Error**  

5. **Added `lock orientation` Option for Camera Rotation in `AutoMove` Mode**  
   - Introduced the `lock orientation` option to allow free camera rotation in `AutoMove` mode.
     - **Enabled (default):** The camera always looks at the next path position.
     - **Disabled:** The camera can be rotated in first-person view using the right mouse button.
   - **Usage:**
     ```Javascript
     // AutoMove settings
     Module.getViewCamera().setAnimationSpeed(1);
     Module.getViewCamera().startAutoMove();
     Module.XDRenderData();

     // Disable to allow free camera movement
     Module.getViewCamera().setLockOrientationAutoMove(false);
     ```
     - For more detailed usage, please refer to the [sandbox sample](https://sandbox.egiscloud.com/code/main.do?id=camera_move_path_visualize).

6. **Added `boundaryLimit` Option for Service Layer**  
   - Introduced the `boundaryLimit` option to restrict object requests within a specified longitude/latitude range when requesting objects in the service layer.
     - **Enabled:** Calls only objects within a predefined range.
       - Even after enabling, you must set the boundary using the `JSLayer::setLimitBoundary()` API.
     - **Disabled (default):** Calls objects as in the existing method.
   - **Usage:**
     ```Javascript
     // Create a service layer in the sandbox
     let layer = Module.getTileLayerList().createXDServerLayer({
       url : "https://xdworld.vworld.kr",
       servername : "XDServer3d",
       name : "facility_build",
       type : 9,
       minLevel : 0,
       maxLevel : 15
     });

     // Set boundary as JSON parameters
     layer.setLimitBoundary({
       boundary: {
         min: [129.125, 35.161],		// Lower left
         max: [129.141, 35.168]		// Upper right
       }
     });

     layer.boundaryLimit = true;   // Enable option
     ```
     - For more detailed usage, please refer to the [sandbox sample](https://sandbox.egiscloud.com/code/main.do?id=layer_request_boundary).

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
