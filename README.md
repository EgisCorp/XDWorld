[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)
### Developers  -  http://www.egiskorea.com/

### Documentation  - https://egiscorp.gitbook.io/xdworld-webgl-manual

### Demos & Sandbox  -  http://sandbox.dtwincloud.com

# Introduction
> WebGL 기반 3D GIS 엔진 XDWORLD ENGINE

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## 특징
> * 웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
> * 멀티 OS, 브라우저, No-Plugin 지원
> * 3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
> * 거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
> * 다양한 도시계획 시뮬레이션 및 분석 기능 제공
> * 공간정보 오픈플랫폼(V World) 데이터 서비스 가능

## 적용분야
> GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등

## Notice
> ### 2022년 4월 11일
> 추후 사용 불가 API 항목 정리 (2023년 01월 01일 까지 지원)
> * SetPlanetImageryType API 
> * changeBaseMap API
> * clearBaseMap API
> * setBaseMapOption API
> * getBaseMapOption API
>
> 사용 불가 API 대체 API 항목 정리
> * Module.GoogleMap();
> * Module.ArcMap();
> * Module.BingMap();
> * Module.DaumMap();
> * Module.MapBox();
> * Module.NaverMap();
> * Module.OpenStreetMap();
> * Module.SKYMap();
> * Module.WMTS();
>
> 변경된 API 샘플 소스는 샌드박스를 참조해 주시면 감사하겠습니다.
> * [샌드박스\_배경지도설정](http://sandbox.dtwincloud.com/code/main.do?id=layer_basemap)
> * [샌드박스\_WMTS](http://sandbox.dtwincloud.com/code/main.do?id=layer_wmts)

## 업데이트
> ### 2022년 7월 19일 (1.37.16)
> * 입력된 영역과 객체의 영역 충돌 체크 조건 추가 (완전 포함, 조금이라도 포함)
> * 라이브맵 1차 
> ### 2022년 7월 14일 (1.37.15)
> * JSMap의 setSimpleMode API 오류 수정
> ### 2022년 7월 13일 (1.37.15)
> * 레이어 별로 건물 심플 모드 설정이 가능한 JSLayer 프로퍼티 simple_real3d 추가
> ```javascript
>var layerList = new Module.JSLayerList(false);
>layer = layerList.nameAtLayer("building_layer_name");
>layer.simple_real3d = true;
> ```
> ### 2022년 7월 08일 (1.37.14)
> * 입력된 영역과 객체의 영역 충돌 체크 오류 수정
> ### 2022년 7월 07일 (1.37.13)
> * 텍스쳐가 없는 Real3d의 색상 변경 API SetDefineMeshColorByObjectKey 미적용 오류 수정
> * JSGhostSymbol의 API exportFileFormat에 XDO 텍스쳐 이미지 파일 지정 기능 추가
> ### 2022년 7월 06일 (1.37.12)
> * 입력된 영역과 객체의 영역 충돌 체크 오류 수정
> * 그림자 분석, 비디오 텍스쳐 기능 오류 수정
> ### 2022년 7월 05일
> * 리소스 URL 설정 API 추가
> * 맵컨트롤을 사용하기 위해서는 [리소스 다운로드](https://github.com/EgisCorp/XDWorld/tree/main/resource/MapCtrl) 해주시기 바랍니다.
> * 리소스 설정 샘플 [샌드박스\_맵컨트롤](http://sandbox.dtwincloud.com/code/main.do?id=option_control_map)
> * 입력된 영역과 객체의 영역 충돌 체크 API 추가
> ### 2022년 6월 29일
> * XDO 포맷 파일 기반 고스트심볼 import 및 export API 추가
> ### 2022년 6월 20일
> * Tile LOD Object 프로토콜 예외처리 추가
> ### 2022년 6월 8일
> * 포인트 클라우드 실시간 높이 조절 기능 구현(Tile LOD Object와 동일)
> * Tile LOD Object 가시화 모듈 수정
> ### 2022년 5월 19일
> * 배경지도 변경 오류 수정
> * 선택 기능 추가
> * JSMap addSelectObject 기능추가
> ### 2022년 4월 27일
> * JSLibraryObject, JSBuildingManager 클래스 API 삭제
> ### 2022년 4월 22일
> * WMTS, 배경지도 오류 수정
> * WMTS 하이브리드 기능 추가
> ### 2022년 4월 21일
> * Real3D 객체 페이스 색상 가시화 모듈 수정
> * JSLineString 좌표 반환 기능 오류 수정 
> ### 2022년 4월 15일
> * Real3D 3DS export 시 메시 방향 지정 오류 수정


