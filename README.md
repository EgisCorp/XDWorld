[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)
### Developers  -  http://www.egiskorea.com/

### Documentation  - https://egiscorp.gitbook.io/xdworld-webgl-manual

### Demos & Sandbox  -  http://sandbox.dtwincloud.com

# Introduction
> WebGL 기반 3D GIS 엔진 XDWORLD ENGINE

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## 특징
 * 웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
 * 멀티 OS, 브라우저, No-Plugin 지원
 * 3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
 * 거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
 * 다양한 도시계획 시뮬레이션 및 분석 기능 제공
 * 공간정보 오픈플랫폼(V World) 데이터 서비스 가능

## 적용분야
 * GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등

## Notice
### 2022년 8월 25일
#### 전광판 객체 기능 보완
 * 여러개의 전광판 설치 및 culling을 통한 비디오 on/off 기능 추가
 * [샌드박스\_전광판](http://sandbox.dtwincloud.com/code/main.do?id=object_ledboard)

### 2022년 8월 24일
#### 아래 API에 대한 callback 함수 삭제
 * 매 프레임마다 callback 불필요하고 API 자체에서 에러메시지 반환되기 때문에 삭제
 * CJSAnalysis::createVideoTexture API
 * CJSFigure::setBoardVideoTexture API

### 2022년 4월 11일
#### 추후 사용 불가 API 항목 정리 (2023년 01월 01일 까지 지원)
 * SetPlanetImageryType API 
 * changeBaseMap API
 * clearBaseMap API
 * setBaseMapOption API
 * getBaseMapOption API

#### 사용 불가 API 대체 API 항목 정리
 * Module.GoogleMap();
 * Module.ArcMap();
 * Module.BingMap();
 * Module.DaumMap();
 * Module.MapBox();
 * Module.NaverMap();
 * Module.OpenStreetMap();
 * Module.SKYMap();
 * Module.WMTS();

#### 변경된 API 샘플 소스는 샌드박스를 참조해 주시면 감사하겠습니다.
 * [샌드박스\_배경지도설정](http://sandbox.dtwincloud.com/code/main.do?id=layer_basemap)
 * [샌드박스\_WMTS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wmts)

## 1.39.0 업데이트 (2022년 12월 14일)
### [새로 추가 된 API]
* void moveTarget(object options)
  * 지정한 방향으로 타겟 오브젝트를 이동시킵니다. (이슈 https://github.com/EgisCorp/XDWorld/issues/236)
  * Class : JSTraceTarget
  * Parameter
      * options : 오브젝트 이동 방향 (front : 전진, back : 후진, left : 왼쪽, right : 오른쪽, up : 상승, down : 하강)
  * Example
      ``` javascript
          trace.moveTarget({
                 left : 0.1,
                 front : 0.1,
                 up : 0.5
          });
      ``` 
* void unionTargetToTerrain()
  * 오브젝트 위치를 지형과 결합시킵니다. 
  * Class : JSTraceTarget
  
### [기능 개선]
* wmts 하이브리드 로드 오류 수정

### [샌드박스]
* 'DEM 경사 조정' 추가(http://sandbox.dtwincloud.com/code/main.do?id=terrain_slope_rate)
* '카메라 경로 가시화' 추가(http://sandbox.dtwincloud.com/code/main.do?id=camera_move_path_visualize)

## 이전 버전 업데이트

<details><summary>1.38.0</summary>
<p>

## 1.38.0 업데이트 (2022년 12월 7일)
### [새로 추가 된 API]
**1. 레이어 별 클릭 지점 및 선택 오브젝트 리턴 API**
>**object pick(unsinged int screenX, unsigned int screenY)**
>* class : JSLayer
>* parameter
>    * screenX : 화면 x 좌표
>    * screenY : 화면 y 좌표
>* return : 피킹 지점이 없는 경우 null 반환, 피킹 지점이 있는 경우 충돌한 오브젝트 키와 위치 좌표 반환함
>* 참고 : (https://github.com/EgisCorp/XDWorld/issues/224)

**2. JSObject 내 오브젝트 속성 정보 저장 및 반환 기능**
>**bool setProperty(string name, number/string value)**
>* class : JSObject
>* parameter
>    * name : 속성 구분 이름
>    * value : 속성 값 (문자, 숫자 정보만 저장 가능)
>* return : 설정 성공 여부
>
>**number/string getProperty(string name)**
>* class : JSObject
>* parameter
>    * name : 속성 구분 이름
>* return : 저장한 속성 값 (속성 값이 존재하지 않는 경우 null 반환)

**3. Round 자동이동 위치 세그먼트 설정 프로퍼티 추가**
>* JSCamera 클래스 내 autoMoveRoundSegment 프로퍼티가 추가됨.
>* 기존 setAutoMoveRoundPositions API는 500개의 고정 된 이동 경로 점을 반환하였으나, autoMoveRoundSegment 파라미터를 통해 이동 경로 지점 수를 설정 가능하도록 수정됨.
>* 세그먼트 수가 적을 수록 지점 간격이 넓어져 이동 속도가 빨라짐.

**4. 3D 그리드 애니메이션 메쉬의 기준 높이 설정 API 추가**
>**void setBaseAltitude(float fAlt)**
>* 지정된 해발고도를 기준높으로 3d 그리드 표현을 시작
>* class : JSGridAnal
>* parameter
>    * fAlt : 기준 높이 값

**5. 그리드 범례 절대값 설정 API 추가**
>**void setLegendMode(int _nMode)**
>* class : JSGridAnal
>* parameter
>    * _nMode : 그리드 범례 절대값
>        * 0 : 상대값 (%) 적용
>        * 1 : 절대값 (val) 적용
>
>**bool setLegendJSON(object _options)**
>* class : JSGridAnal    
>* parameter
>    * _options : 설정 속성 값
>        * 입력형식 { legendMode : Number, legend : [ { val : Number, color : { a, r, g, b ] }, { val : Number, color : { a, r, g, b ] }, ...] }
>* setLegendMode 및 컬러테이블 설정

**6. JSGridAnal 클래스 내 단일 시간 다중 분석 그리드 객체에 대한 병합기능 추가**
>**void openMultipleGridDataURL(string szURL, unsigned int nTime, unsigned int nStripSize, unsigned int nStripStart, unsigned int nStripEnd, unsigned char nDataType, unsigned char nMultipleCnt, unsigned char nMultipleIndex)**
>* class : JSGridAnal
>* parameter
>    * szURL : 데이터 요청 URL 
>    * nTime : 시간 인덱스 (0-base)
>    * nStripSize :  그리드 하나의 셀의 byte 크기
>    * nStripStart : 그리드 셀에서 데이터 인식 offset 시작 byte (0-base)
>    * nStripEnd : 그리드 셀에서 데이터 인식 offset 종료 byte (0-base), nStripEnd - nStripStart가 데이터 바이트 크기
>    * nDataType : 데이터 자료형 (0 : int, 1 : float, 2 : double)
>    * nMultipleCnt : 다중 중첩 수 
>    * nMultipleIndex : 다중 중첩 인덱스
>* 그리드 필드 하나에 연결된 모든 데이터 필드를 합산하여 표현

**7. JSGridAnal 클래스 내 마우스 클릭시 격자 정보 콜백기능 추가**
>**void setMouseCallback(function _callback)**
>* 그리드 데이터 로드후 마우스 왼쪽버튼을 통한 버튼 업에서 지정된 콜백 호출
>* class : JSGridAnal
>* parameter
>    * _callback : 콜백 함수
>        * 콜백 반환 인자 : { longitude : Number, latitude : Number, idx : Number, idy : Number, value : Number , angle : Number }

**8. JSGridAnal 클래스 내 격자 3D 라인 출력기능 추가**
>**void setGridLineVisible(boolean _visible)**
>* 그리드 라인 표현 여부 설정
>* class : JSGridAnal
>* parameter
>    * _visible : 가시화 설정 값
>
>**void setGridLineBaseAlt(float _fAltitude)**
>* 그리드 라인의 기준 표현 해발고도 설정
>* class : JSGridAnal
>* parameter
>    * _fAltitude : 기준 표현 해발고도
>
>**void setGridLineMaxDistance(float _fDistance)**
>* 그리드 라인의 최대 표현 해발고도, 최대표현부터 기준고도까지 거리별(%)로 알파 적용
>* class : JSGridAnal
>* parameter
>    * _fDistance : 그리드 라인의 최대 표현 해발고도

**9. Canvas style left, top 옵션에 따른 마우스 위치 처리 기능 추가**
>**void ApplyCanvasPosition()**
>* Canvas style 변경 시 동기화 실행
>* Canvas 위치 변경에 따른 HTMLObject 위치 조정 적용
>* class : Module

**10. JSColorGrid 투명도 조절 API 추가**
>**void setOpacity(float _opacity)**
>* class : JSColorGrid
>* parameter
>    * _opacity : 투명도 (0.0~1.0 사이 값 적용)

**11. JSColorPolygon 투명도 조절 API 추가**
>**void setOpacity(float _opacity)**
>* class : JSColorPolygon
>* parameter
>    * _opacity : 투명도 (0.0~1.0 사이 값 적용)

### [개선 된 기능]
>* 화면 분할 시 POI 라인이 단독 렌더링되는 현상 수정 (https://github.com/EgisCorp/XDWorld/issues/230)
>* JSGridAnal 클래스에 단일 시간 분석 그리드 객체에 대한 표출기능 추가
>* 중복키 이벤트 처리 추가(https://github.com/EgisCorp/XDWorld/issues/218)
> * 화면 분할 시 POI 라인이 단독 렌더링되는 현상 수정(https://github.com/EgisCorp/XDWorld/issues/230)
> * 마우스 클릭지점 이격 오류 수정

</p>
</details>

<details><summary>1.37.43</summary>
<p>

### 2022년 12월 1일 (1.37.43)
 * 카메라 회전 예외 처리 추가
</p>
</details>

<details><summary>1.37.42</summary>
<p>

### 2022년 11월 28일 (1.37.42)
 * ([이슈#223](https://github.com/EgisCorp/XDWorld/issues/223)) 해결
</p>
</details>

<details><summary>1.37.41</summary>
<p>

### 2022년 11월 25일 (1.37.41)
 * 지형그리드 생성 모듈 수정
</p>
</details>

<details><summary>1.37.40</summary>
<p>

### 2022년 11월 18일 (1.37.40)
 * HTMLObject 정렬 기능에 따른 위치 조정 기능 추가
 * Real3D 단면도 출력 API 추가
 * 카메라 지하 이동 시 고정 배경 색상 지정 부분 수정
 * 2D 바 그래프 소수점 자릿수 설정 기능 추가
 * 값이 0인 2D 바 그래프 수치 텍스트 표시 
</p>
</details>

<details><summary>1.37.39</summary>
<p>

### 2022년 10월 31일 (1.37.39)
 * 객체 투명도 편집 오류 수정
</p>
</details>

<details><summary>1.37.38</summary>
<p>

### 2022년 10월 26일 (1.37.38)
 * 객체 Fill, Stroke 모드 오류 수정
</p>
</details>

<details><summary>1.37.37</summary>
<p>

### 2022년 10월 21일 (1.37.37)
 * RTT Line 투명값 수정되지 않는 현상 수정
</p>
</details>

<details><summary>1.37.36</summary>
<p>

### 2022년 10월 20일 (1.37.36)
 * 마우스 선택 모드에서 오브젝트가 선택되지 않는 현상 수정
</p>
</details>

<details><summary>1.37.35</summary>
<p>

### 2022년 10월 12일 (1.37.35)
 * JSLayer에 횡단면 출력 기능 사용 여부 설정 API setReal3dCutUse 추가 
 * JSLayer에 횡단면 출력 기능 높이 설정 API setReal3dCutHeight 추가 
</p>
</details>

<details><summary>1.37.33</summary>
<p>

### 2022년 10월 6일 (1.37.33)
 * JSFlowPolygon 좌표 정보 반환 프로퍼티 'coordinates' 추가
 * 포인트-라인 간 최단 거리 계산 API getClosestPositionOnPath 추가
</p>
</details>

<details><summary>1.37.32</summary>
<p>

### 2022년 10월 5일 (1.37.32)
 * JSFlowPolygon/JSPolygon 오브젝트 선택 오류 수정
 * 바람길 기능 수정
   * 빌딩관련 NoData 값 변경( 999 -> 0 )
   * 토지피복도 관련 기능 추가
</p>
</details>

<details><summary>1.37.31</summary>
<p>

 ### 2022년 9월 30일 (1.37.31)
 * wfs poi, poi 인코딩 문제 수정
</p>
</details>

<details><summary>1.37.30</summary>
<p>

### 2022년 9월 26일 (1.37.30)
 * JSBarGraph3D 텍스트 텍스쳐 렌더링 오류 수정
</p>
</details>

<details><summary>1.37.29</summary>
<p>

### 2022년 9월 23일 (1.37.29)
 * 메뉴얼 업데이트 JSTerrain, JSMath
 * Module.getTerrain().makeTerrainElevationCellData("parameter") 추가
   * 그리드 생성 기능 
 * Module.getMath().calculationSlopeAnalysis("parameter") 추가
   * [3 * 3] 배열값을 통한 경사 분석 기능
 * Module.getMap().ScreenToMapPointEX API 실행 시 피킹점이 없는 경우 null 반환하도록 루틴 추가([이슈#211](https://github.com/EgisCorp/XDWorld/issues/211))
</p>
</details>

<details><summary>1.37.28</summary>
<p>

### 2022년 9월 22일 (1.37.28)
 * 비디오 텍스쳐 Zoom In/Out 기능 추가

 * 버텍스 및 인덱스가 활용 된 JSColorPolygon의 마우스 피킹 기능 수정
 * 3D POI 텍스트의 문자 셋 지정 프로퍼티 추가
 ```javascript
var layerList = new Module.JSLayerList(false);
var layer = layerList.nameAtLayer("POI 텍스트 타일 레이어 이름");
layer.text_character_set = "EUC-KR";   // 디폴트 셋은 UTF-8
 ```
</p>
></details>

<details><summary>1.37.27</summary>
<p>

### 2022년 9월 14일 (1.37.27)
 * JSColorPolygon의 마우스 피킹 기능 추가
</p>
</details>

<details><summary>1.37.26</summary>
<p>

### 2022년 9월 02일 (1.37.26)
 * ([이슈#203](https://github.com/EgisCorp/XDWorld/issues/203)) 해결
</p>
</details>

<details><summary>1.37.23</summary>
<p>

### 2022년 8월 24일 (1.37.23)
 * 비디오 텍스쳐 메모리 누수 관련 오류 수정
 * ([비디오텍스쳐](http://sandbox.dtwincloud.com/code/main.do?id=object_video_texture))
 * ([전광판](http://sandbox.dtwincloud.com/code/main.do?id=object_ledboard))
</p>
</details>

<details><summary>1.37.22</summary>
<p>

### 2022년 8월 23일 (1.37.22)
 * 터치 이동/회전/줌인&아웃 사용 설정 프로퍼티 추가([이슈 200](https://github.com/EgisCorp/XDWorld/issues/200))
 ```javascript
// 터치 이동 활성화(true), 비활성화(false)
Module.getControl().touchPanEnable = true; 

// 터치 회전 활성화(true), 비활성화(false)
Module.getControl().touchRotateEnable = true; 

// 터치 줌 인&아웃 활성화(true), 비활성화(false)
Module.getControl().touchZoomEnable = true; 

 ```
</p>
></details>

<details><summary>1.37.21</summary>
<p>

### 2022년 8월 19일 (1.37.21)
 * setDescription, getDescription uft16 지원([이슈 197](https://github.com/EgisCorp/XDWorld/issues/197))
</p>
</details>

<details><summary>1.37.20</summary>
<p>

### 2022년 8월 04일 (1.37.20)
 * 고스트심볼(JSGhostSymbol) z버퍼 off 프로퍼티 추가([이슈 194](https://github.com/EgisCorp/XDWorld/issues/194))
 ```javascript
var object = Module.createGhostSymbol("MY_OBJECT");
object.zBufferOff = true;
 ```
</p>
</details>

<details><summary>1.37.19</summary>
<p>

### 2022년 8월 04일 (1.37.19)
 * 건물 객첵 key List 기반 색상 변경 API 추가
</p>
</details>

<details><summary>1.37.18</summary>
<p>

### 2022년 8월 02일 (1.37.18)
 * 실시간 cctv 관제 편집기능 추가
</p>
</details>

<details><summary>1.37.17</summary>
<p>

### 2022년 7월 26일 (1.37.17)
 * 가시권 분석 이슈 처리([이슈 189](https://github.com/EgisCorp/XDWorld/issues/189))
</p>
</details>

<details><summary>1.37.16</summary>
<p>

 ### 2022년 7월 19일 (1.37.16)
 * 입력된 영역과 객체의 영역 충돌 체크 조건 추가 (완전 포함, 조금이라도 포함)
 * 라이브맵 1차 

### 2022년 7월 14일 (1.37.16)
 * JSMap의 setSimpleMode API 오류 수정
</p>
</details>

<details><summary>1.37.15</summary>
<p>

### 2022년 7월 13일 (1.37.15)
 * 레이어 별로 건물 심플 모드 설정이 가능한 JSLayer 프로퍼티 simple_real3d 추가
 ```javascript
var layerList = new Module.JSLayerList(false);
layer = layerList.nameAtLayer("building_layer_name");
layer.simple_real3d = true;
 ```
</p>
</details>

<details><summary>1.37.14</summary>
<p>

### 2022년 7월 08일 (1.37.14)
 * 입력된 영역과 객체의 영역 충돌 체크 오류 수정
</p>
</details>

<details><summary>1.37.13</summary>
<p>

### 2022년 7월 07일 (1.37.13)
 * 텍스쳐가 없는 Real3d의 색상 변경 API SetDefineMeshColorByObjectKey 미적용 오류 수정
 * JSGhostSymbol의 API exportFileFormat에 XDO 텍스쳐 이미지 파일 지정 기능 추가
</p>
</details>

<details><summary>1.37.12</summary>
<p>

### 2022년 7월 06일 (1.37.12)
 * 입력된 영역과 객체의 영역 충돌 체크 오류 수정
 * 그림자 분석, 비디오 텍스쳐 기능 오류 수정
</p>
</details>

<details><summary>이전 버전 업데이트</summary>
<p>

### 2022년 7월 05일
 * 리소스 URL 설정 API 추가
 * 맵컨트롤을 사용하기 위해서는 [리소스 다운로드](https://github.com/EgisCorp/XDWorld/tree/main/resource/MapCtrl) 해주시기 바랍니다.
 * 리소스 설정 샘플 [샌드박스\_맵컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_map)
 * 입력된 영역과 객체의 영역 충돌 체크 API 추가
### 2022년 6월 29일
 * XDO 포맷 파일 기반 고스트심볼 import 및 export API 추가
 ### 2022년 6월 20일
 * Tile LOD Object 프로토콜 예외처리 추가
### 2022년 6월 8일
 * 포인트 클라우드 실시간 높이 조절 기능 구현(Tile LOD Object와 동일)
 * Tile LOD Object 가시화 모듈 수정
### 2022년 5월 19일
 * 배경지도 변경 오류 수정
 * 선택 기능 추가
 * JSMap addSelectObject 기능추가
### 2022년 4월 27일
 * JSLibraryObject, JSBuildingManager 클래스 API 삭제
### 2022년 4월 22일
 * WMTS, 배경지도 오류 수정
 * WMTS 하이브리드 기능 추가
### 2022년 4월 21일
 * Real3D 객체 페이스 색상 가시화 모듈 수정
 * JSLineString 좌표 반환 기능 오류 수정 
### 2022년 4월 15일
 * Real3D 3DS export 시 메시 방향 지정 오류 수정
</p>
</details>
