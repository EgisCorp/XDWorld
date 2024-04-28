[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation
  * [Korean] https://egiscorp.gitbook.io/xdworld-webgl-manual
### Demos & Sandbox - https://sandbox.egiscloud.com
### Demos & Sandbox (beta) : https://sandbox.egiscloud.com/code/main.do?id=start&engine=beta&worker=true

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

### 1.61.0 (2024/4/26)

#### 1. 수인한도분석 상세분석 옵션 추가
  * '수인한도분석' 기능에서, 상세한 분석을 위한 `isdetail` 프로퍼티가 추가되었습니다.
    * true: 그리드 영역에 햇빛이 들지 않는 영역이 있을 경우, 일조량 계산하지 않음.
    * false:절반이상 햇빛이 들면 일조량 계산.

#### 2. HeatMap API에 가중치 매개변수 추가
  - 기존 히트맵 정보를 입력하는 API의 매개변수에 `가중치`가 추가되었습니다.
  - addHeatMapEX(JSVector3D(경도, 위도, 가중치)) : JSMap 클래스
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // 히트맵 설정
      for(var i=0; i<4000; ++i)
      {
          pMap.addHeatMapEX(new Module.JSVector3D(124.0+Math.random()*8.0, 34.0+Math.random()*6.0, 1.0));
      }
    ```
  - addHeatMapsEX(JSVec3Array(경도, 위도, 가중치)) : JSMap 클래스
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // 히트맵 설정
      var vList = new Module.JSVec3Array();
        
      vList.push(new Module.JSVector3D(128.388791, 36.398409, 1.0));
      vList.push(new Module.JSVector3D(126.745337, 35.019302, 2.0));
      vList.push(new Module.JSVector3D(128.902455, 35.319581, 3.0));
      vList.push(new Module.JSVector3D(129.147955, 36.119326, 4.0));
      vList.push(new Module.JSVector3D(129.073899, 37.210022, 5.0));
      vList.push(new Module.JSVector3D(128.373239, 37.765977, 6.0));
      vList.push(new Module.JSVector3D(127.108525, 37.658713, 7.0));
      vList.push(new Module.JSVector3D(126.256902, 36.562545, 8.0));
      vList.push(new Module.JSVector3D(127.445746, 36.108470, 9.0));
      vList.push(new Module.JSVector3D(127.820355, 36.789230, 10.0));
      vList.push(new Module.JSVector3D(127.033226, 37.521304, 1.0));
      vList.push(new Module.JSVector3D(127.042107, 37.520151, 1.0));
      vList.push(new Module.JSVector3D(127.044620, 37.514160, 1.0));
      vList.push(new Module.JSVector3D(127.048812, 37.518277, 1.0));
      vList.push(new Module.JSVector3D(127.030439, 37.506783, 1.0));
      vList.push(new Module.JSVector3D(127.028751, 37.505695, 1.0));

      pMap.addHeatMapsEX(vList);
      pMap.setEffectDistance(2000000);
    ```

### 1.60.1 / beta 2.2.1 (2024/4/22)

#### 1. JSPolygon 텍스쳐 매핑 옵션 추가
  * JSPolygon의 Face에 텍스쳐 이미지 적용 시 타일 매핑 설정이 가능하도록 API가 추가되었습니다.
  * Clamp to Edge / Repeat / Mirrored Repeat 옵션이 설정 가능합니다.
  * 각 옵션 값 상수를 Module 객체를 통해 적용하실 수 있습니다.

  * bool setFaceTextureWrapU(number _face_index, int _wrap_type)
    * Face의 텍스쳐 u좌표(이미지 가로 x 좌표와 매칭)의 타일링 옵션을 설정하는 함수입니다.
    * Class : JSPolygon
    * Prarmeter
      * _face_index (number) : 적용하고자 하는 JSPolygon의 face index
      * _wrap_type (number) : 텍스쳐 타일링 타입(Clamp to Edge / Repeat / Mirrored Repeat)

  * bool setFaceTextureWrapV(number _face_index, int _wrap_type)
    * Face의 텍스쳐 v좌표(이미지 가로 y 좌표와 매칭)의 타일링 옵션을 설정하는 함수입니다.
    * Class : JSPolygon
    * Parameter
      * _face_index (number) : 적용하고자 하는 JSPolygon의 face index
      * _wrap_type (number) : 텍스쳐 타일링 타입(Clamp to Edge / Repeat / Mirrored Repeat)

  ``` javascript
  function setPolygonTextureWrapType(_polygon, _face_index, _wrap_type) {

      if (polygon) {
				
          polygon.setFaceTextureWrapU(_face_index, _wrap_type);
          polygon.setFaceTextureWrapV(_face_index, _wrap_type);

          Module.XDRenderData();
      }
  }
  ```

#### 2. 측량(Straight-Line Distance) 기능 수정
  * 건물 위를 둘러싸는 직선이 삭제되었습니다.

#### 3. JSLayer에서 타일레이어의 타일로딩 완료 콜백 추가
  * JSLayer에서 타일레이어의 타일로딩 완료 이벤트 콜백 함수가 추가되었습니다.
  * XDServer를 통해서 서비스 받는 타일레이어 ( [Module.getTileLayerList()](https://egiscorp.gitbook.io/xdworld-webgl-manual/introduce-1/layer/jslayerlist#createxdserverlayer-option-jslayer) ) 대상으로 적용됩니다.
  * 레이어 속 타일에 대한 로딩시 식별객체가 함께 로딩되는 타입들 ( TILE_LAYER_TYPE_POI, TILE_LAYER_TYPE_GHOST_SYMBOL, TILE_LAYER_TYPE_VECTOR_PIPE,  TILE_LAYER_TYPE_REAL3D_PACK)은 **타일 로드 완료시 콜백이 발생**하며 TILE_LAYER_TYPE_REAL3D인 경우는 타일로드 후에 모델링 데이터를 로딩하기에 **각 개별 모델이 로딩시 콜백이 발생**합니다.
  * JSLayer::setTileLoadCallback( _callbackFunc ) 으로 사용할 수 있습니다.
 
```
// 콜백 파라메터 구조
idx : number
idy : number
layerName : string
layerType :  number
level :  number 
objectList :  array [ objectKey1 (string), objectKey2 (string), ... ]
```


```
// 테스트 샘플
let gLayer = null;   // 객체 추출을 위한 레이어 변수
function loadCallback(e)
{
	console.log(e);
	e.objectList.forEach((objkey) => {
		let obj = gLayer.keyAtObject(objkey);               // 키를 통한 레이어에서 객체 인터페이스 반환
		if(obj != null && obj.getObjectType() == 8) {   // Real3D 개체 타입 확인
			obj.setFillColor(false, new Module.JSColor(255, 64, 255, 64));   // 색상 변경
		}
	});
}
function loadFacility3D() {
	var layer = Module.getTileLayerList().createXDServerLayer({
		url : "https://xdworld.vworld.kr",
		servername : "XDServer3d",
		name : "facility_build",
		type : 9,
		minLevel : 0,
		maxLevel : 15
	});

	layer.setTileLoadCallback(loadCallback);  // 콜백 적용
	gLayer = layer;
}
```

### 1.61.0 (2024/4/26)

#### 1. Detailed Analysis Option Added to Solar Limit Analysis
  * In 'solar limit analysis' feature, a isdetail property has been added for more detailed analysis.
    * true: Do not calculate insolation if there is an area in the grid where sunlight does not reach.
    * false: Calculate insolation if more than half of the area receives sunlight.

#### 2. Weight Parameter Added to HeatMap API
  - `weight` parameter has been added to the parameters of the API for inputting existing heatmap information.
  - addHeatMapEX(JSVector3D(longitude, latitude, weight)) : JSMap class
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // Set HeatMap
      for(var i=0; i<4000; ++i)
      {
          pMap.addHeatMapEX(new Module.JSVector3D(124.0+Math.random()*8.0, 34.0+Math.random()*6.0, 1.0));
      }
    ```
  - addHeatMapsEX(JSVec3Array(longitude, latitude, weight)) : JSMap class
    ```javascript
      var pMap = Module.getMap();
      pMap.setTerrainEffect(9); // Set HeatMap
      var vList = new Module.JSVec3Array();
        
      vList.push(new Module.JSVector3D(128.388791, 36.398409, 1.0));
      vList.push(new Module.JSVector3D(126.745337, 35.019302, 2.0));
      vList.push(new Module.JSVector3D(128.902455, 35.319581, 3.0));
      vList.push(new Module.JSVector3D(129.147955, 36.119326, 4.0));
      vList.push(new Module.JSVector3D(129.073899, 37.210022, 5.0));
      vList.push(new Module.JSVector3D(128.373239, 37.765977, 6.0));
      vList.push(new Module.JSVector3D(127.108525, 37.658713, 7.0));
      vList.push(new Module.JSVector3D(126.256902, 36.562545, 8.0));
      vList.push(new Module.JSVector3D(127.445746, 36.108470, 9.0));
      vList.push(new Module.JSVector3D(127.820355, 36.789230, 10.0));
      vList.push(new Module.JSVector3D(127.033226, 37.521304, 1.0));
      vList.push(new Module.JSVector3D(127.042107, 37.520151, 1.0));
      vList.push(new Module.JSVector3D(127.044620, 37.514160, 1.0));
      vList.push(new Module.JSVector3D(127.048812, 37.518277, 1.0));
      vList.push(new Module.JSVector3D(127.030439, 37.506783, 1.0));
      vList.push(new Module.JSVector3D(127.028751, 37.505695, 1.0));

      pMap.addHeatMapsEX(vList);
      pMap.setEffectDistance(2000000);
    ```

### 1.60.1 / beta 2.2.1 (2024/4/22)

#### 1. Added JSPolygon Texture Mapping Options
  * Added an API to enable tile mapping settings when applying texture images to faces of JSPolygon.
  * Options for Clamp to Edge / Repeat / Mirrored Repeat are now available.
  * Each option value constant can be applied through the Module object.
  * bool setFaceTextureWrapU(number _face_index, int _wrap_type)
    * Function to set tiling options for the u-coordinate of the texture (matching the horizontal x-coordinate of the image) of a face.
    * Class: JSPolygon
    * Parameters
      * _face_index (number): Face index of the JSPolygon to which the setting should be applied.
      * _wrap_type (number): Texture tiling type (Clamp to Edge / Repeat / Mirrored Repeat).

  * bool setFaceTextureWrapV(number _face_index, int _wrap_type)
    * Function to set tiling options for the v-coordinate of the texture (matching the vertical y-coordinate of the image) of a face.
    * Class: JSPolygon
    * Parameters
      * _face_index (number): Face index of the JSPolygon to which the setting should be applied.
      * _wrap_type (number): Texture tiling type (Clamp to Edge / Repeat / Mirrored Repeat).

  ```javascript
  function setPolygonTextureWrapType(_polygon, _face_index, _wrap_type) {

    if (polygon) {
  			
        polygon.setFaceTextureWrapU(_face_index, _wrap_type);
        polygon.setFaceTextureWrapV(_face_index, _wrap_type);

        Module.XDRenderData();
    }
  }
  ```

#### 2. Modified Straight-Line Distance Feature
  * The straight lines encompassing buildings have been removed.

#### 3. Added Tile Loading Completion Callback in JSLayer
  * Added an event callback function for tile loading completion in JSLayer.
  * Applicable to tile layers serviced through XDServer (Module.getTileLayerList()).
  * For types where identification objects are loaded along with tiles (TILE_LAYER_TYPE_POI, TILE_LAYER_TYPE_GHOST_SYMBOL, TILE_LAYER_TYPE_VECTOR_PIPE, TILE_LAYER_TYPE_REAL3D_PACK), callbacks occur upon tile load completion, and for TILE_LAYER_TYPE_REAL3D, callbacks occur upon individual model loading after tile load.
  * Can be used with JSLayer::setTileLoadCallback( _callbackFunc ).
  
   ```javascript
  // Callback parameter structure
  idx: number
  idy: number
  layerName: string
  layerType: number
  level: number
  objectList: array [objectKey1 (string), objectKey2 (string), ...]
  ```

  ```javacript
  // Test sample
  let gLayer = null; // Layer variable for object extraction
  function loadCallback(e)
  {
    console.log(e);
    e.objectList.forEach((objkey) => {
      let obj = gLayer.keyAtObject(objkey); // Returns the object interface in the layer through the key
      if(obj != null && obj.getObjectType() == 8) { // Check Real3D object type
        obj.setFillColor(false, new Module.JSColor(255, 64, 255, 64)); // Change color
      }
    });
  }
  function loadFacility3D() {
    var layer = Module.getTileLayerList().createXDServerLayer({
      url : "https://xdworld.vworld.kr",
      servername : "XDServer3d",
      name : "facility_build",
      type : 9,
      minLevel : 0,
      maxLevel : 15
    });

    layer.setTileLoadCallback(loadCallback); // Apply callback
    gLayer = layer;
  }
  ```

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
