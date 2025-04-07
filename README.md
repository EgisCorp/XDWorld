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

$\huge{\rm{\color{red}Important\ note}}$

$\rm{\color{red}●\ 1인칭\ 카메라\ 비디오\ 텍스쳐\ 기능\ 지원\ 중단}$
  * 기존 1인칭 카메라 비디오 텍스쳐 기능은 2025년까지 지원합니다. 
  * JSCamera 클래스의 삭제 API ---------> JSVideoObject 클래스의 대체 API 
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera 클래스의 삭제 property ---------> JSVideoObject 클래스의 대체 property</summary>
     
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
   </details>

  * 비디오 객체  [비디오 객체](https://sandbox.egiscloud.com/code/main.do?id=object_video), [전광판](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), [RTT 비디오](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture)를 참고하시기 바랍니다.

$\rm{\color{red}●\ Discontinuation\ of\ First-Person\ Camera\ Video\ Texture\ Feature}$
  * The existing First-Person Camera Video Texture feature will be supported until 2025.
  * JSCamera class removal API ---------> Replacement API in JSVideoObject class
    - [x] setVideoInfo ---------> createVideo
    - [x] clearVideo -----------> clearTexture
    <details>
     <summary>JSCamera class removal properties ---------> Replacement properties in JSVideoObject class</summary>
     
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
   </details>

  * Please refer to [Video Object](https://sandbox.egiscloud.com/code/main.do?id=object_video), [LED Board](https://sandbox.egiscloud.com/code/main.do?id=object_ledboard), and [RTT Video](https://sandbox.egiscloud.com/code/main.do?id=object_polygon_rtt_video_image_texture).

## Update

- 다음 배포 일정: **2025년 05월 06일(월)**
- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.

### 2.13.0 (2025/04/07)

1. 터파기 가시화 오브젝트 추가(https://github.com/EgisCorp/XDWorld/issues/476)
     * 기존 JSColorPipe 뿐만 아니라 JSFlowPolygon, JSPolygon, JSReal3d(건물) 오브젝트도 원형 터파기 영역에 보이도록 기능을 추가하였습니다.
     * 보이고자 하는 JSLayer의 setViewInTransparency API를 통해 보이기 여부를 설정할 수 있습니다.
     * 기본 값은 보이지 않음(false) 이며, JSColorPipe 객체는 예외적으로 보임 상태를 유지합니다.
     * void setViewInTransparency(bool _set)
       * Class : JSLayer
       * Parameter
         * _set(bool) : 보이기 여부(true 보임 / false 보이지 않음)
       ``` javascript
       layer.setViewInTransparency(true);
       ```
     * bool getViewInTransparency();
       * Class : JSLayer
       * Return
         * 보임 설정 여부(bool)
       ``` javascript
       var visible = layer.getViewInTransparency();
       ```

2. JSPolygon의 Union mode 오류 수정 (https://github.com/EgisCorp/XDWorld/issues/478)
    - JSPolygon에 Union mode 설정 후 RTT 적용이 되지 않는 점을 수정하였습니다.

3. 라인 효과 추가 및 정리
     - 라인 타입에 따른 옵션 및 매개변수 구조를 보다 사용하기 쉽도록 수정하였습니다.
     - 변경 사항
       - type: 기존 숫자로 입력하는 방식에서 Module.BLING (type: NORMAL, OUTLINE, GLOW, ARROW, DASH, FIRE, BLING, WARNING)등의 상수로 정의하도록 변경되었습니다.
       - animation, loopcount 속성을 추가하여 가시화 효과(type)에 따라 애니메이션 효과가 적용되도록 변경되었습니다.
     - 라인 크기를 고정시키는 옵션을 추가하였습니다.
     ```javascript
     [기존방식]
     let data = {
       coordinates: coordinates,
       type: 0,						// Solid line creation
       union: false,						// Terrain union status
       depth: true,						// Object overlap status
       color: new Module.JSColor(255, 255, 0, 0),		// ARGB
       width: 1,						// Line width
     };

     [변경된 방식]
     let data = {
       coordinates: coordinates,
       type: Module.BLING,					// Solid line creation
       union: false,						// Terrain union status
       depth: true,						// Object overlap status
       color: new Module.JSColor(255, 255, 0, 0),		// ARGB
       width: 1,						// Line width
       animation: true,					// Animation
       sizefix: true,						// size fixed
       loopcount: 1						// Animation loop count
     };
     ```

4. POI 가시화 오류 수정

     - 카메라 영역을 벗어날 경우, POI가 화면에서 사라지는 오류를 수정하였습니다.
     - 이제부터 영역을 벗어나면 POI 높이를 조절하여 화면 내부에서 볼 수 있도록 변경됩니다.

5. 빌보드 회전 타입 추가
     * 아래 이미지와 같이 지면과 수평한 빌보드의 회전 타입이 추가되었습니다.
       ![Image](https://github.com/user-attachments/assets/4002a632-4efe-4ba7-8bec-9382c1402d48)
     * JSBillboard의 setRotationMode API를 통해 mode 2번을 선택하시면 적용하실 수 있습니다.
       ``` javascript
       billboard.setRotationMode(2);
       ```

6. 마우스 조작 이벤트 버튼 설정 기능 추가
     * 마우스 버튼을 통해 지도 조작(이동, 회전, 줌) 동작에 사용할 버튼을 설정할 수 있도록 하는 기능이 추가되었습니다.  
     * `setMouseControlEvent`를 통해 조작 타입별 버튼을 설정할 수 있으며, `getMouseControlEvent`로 현재 설정된 버튼 값을 조회할 수 있습니다.  
     * 조작 타입은 `"translate"`, `"rotate"`, `"zoom"` 중 하나이며, 버튼 값은 0(좌클릭), 1(휠클릭), 2(우클릭) 중 하나입니다.  
     * `bool setMouseControlEvent(string type, int button)`  
       * Class : JSControl  
       * Parameter  
         * `type` (string) : 조작 타입 ("translate", "rotate", "zoom")  
         * `button` (int) : 마우스 버튼 값 (0: 좌클릭, 1: 휠클릭, 2: 우클릭)  
       * Return  
         * 설정 성공 여부 (bool)  
       ```javascript
       JSControl.setMouseControlEvent("rotate", 2);  // 회전을 우클릭으로 설정
       ```
     * `int getMouseControlEvent(string type)`  
       * Class : JSControl  
       * Parameter  
         * `type` (string) : 조작 타입 ("translate", "rotate", "zoom")  
       * Return  
         * 해당 타입의 현재 마우스 버튼 값 (int)  
       ```javascript
       var zoomButton = JSControl.getMouseControlEvent("zoom");
       ```

### 2.13.0 (2025/04/07)

1. **Excavation Visualization Object Added**  
   (https://github.com/EgisCorp/XDWorld/issues/476)
   * In addition to the existing `JSColorPipe`, now `JSFlowPolygon`, `JSPolygon`, and `JSReal3d` (building) objects are also visible within the circular excavation area.
   * Visibility can be toggled via the `setViewInTransparency` API of the relevant `JSLayer`.
   * Default value is `false` (not visible). `JSColorPipe` objects remain visible by default.
   * `void setViewInTransparency(bool _set)`
     * **Class**: JSLayer
     * **Parameter**:
       * `_set (bool)`: Whether to show or hide (true: show / false: hide)
     ```javascript
     layer.setViewInTransparency(true);
     ```
   * `bool getViewInTransparency()`
     * **Class**: JSLayer
     * **Return**:
       * Visibility setting (bool)
     ```javascript
     var visible = layer.getViewInTransparency();
     ```

2. **JSPolygon Union Mode Bug Fix**  
   (https://github.com/EgisCorp/XDWorld/issues/478)
   * Fixed an issue where applying RTT after setting Union mode on a `JSPolygon` did not function correctly.

3. **Line Effects Enhancement and Refactoring**
   * Improved the structure of line type options and parameters for better usability.
   * **Changes**:
     - `type`: Previously used numeric values are now defined using constants such as `Module.BLING` (`type` values: NORMAL, OUTLINE, GLOW, ARROW, DASH, FIRE, BLING, WARNING).
     - `animation` and `loopcount` properties have been added to allow animation effects depending on the line type.
     - Added option to fix line size.

   ```javascript
   // [Previous Method]
   let data = {
     coordinates: coordinates,
     type: 0,                          // Solid line creation
     union: false,                    // Terrain union status
     depth: true,                     // Object overlap status
     color: new Module.JSColor(255, 255, 0, 0),  // ARGB
     width: 1                         // Line width
   };

   // [Updated Method]
   let data = {
     coordinates: coordinates,
     type: Module.BLING,             // Line effect type
     union: false,                   // Terrain union status
     depth: true,                    // Object overlap status
     color: new Module.JSColor(255, 255, 0, 0),  // ARGB
     width: 1,                       // Line width
     animation: true,               // Enable animation
     sizefix: true,                 // Fix line size
     loopcount: 1                   // Number of animation loops
   };
   ```

4. **POI Visualization Bug Fix**
   * Fixed an issue where POIs disappeared when outside the camera area.
   * Now, POI height is adjusted to remain visible within the screen even when outside the camera bounds.

5. **New Billboard Rotation Mode Added**
   * A new billboard rotation mode has been added to allow horizontal alignment with the ground.
     ![Image](https://github.com/user-attachments/assets/4002a632-4efe-4ba7-8bec-9382c1402d48)
   * Apply by using the `setRotationMode` API with mode 2:
     ```javascript
     billboard.setRotationMode(2);
     ```

6. **Mouse Control Event Button Configuration Added**
   * Users can now configure which mouse button (left, middle, right) is used for each type of map control (translate, rotate, zoom).
   * Use `setMouseControlEvent` to assign the button and `getMouseControlEvent` to query it.
   * **Control types**: "translate", "rotate", "zoom"
   * **Button values**: 0 (left click), 1 (middle click), 2 (right click)

   * `bool setMouseControlEvent(string type, int button)`
     * **Class**: JSControl
     * **Parameters**:
       * `type (string)`: Control type ("translate", "rotate", "zoom")
       * `button (int)`: Mouse button value (0: left, 1: middle, 2: right)
     * **Return**:
       * Whether the setting was successful (bool)
     ```javascript
     JSControl.setMouseControlEvent("rotate", 2);  // Set rotate to right-click
     ```

   * `int getMouseControlEvent(string type)`
     * **Class**: JSControl
     * **Parameter**:
       * `type (string)`: Control type
     * **Return**:
       * Current mouse button value assigned to the type (int)
     ```javascript
     var zoomButton = JSControl.getMouseControlEvent("zoom");
     ```

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
