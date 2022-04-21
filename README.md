[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)
### Developers  -  http://www.egiskorea.com/

### Documentation  -  http://api.xdmap.com/Manual

### Demos & Sandbox  -  http://sandbox.dtwincloud.com/code/main.do?id=start

### Latest Release(v.1.36)  -  [https://github.com/EgisCorp/XDWorld/tree/v_1.36.6](https://github.com/EgisCorp/XDWorld/tree/v_1.36.6)

# Introduction
> WebGL 기반 3D GIS 엔진 XDWORLD ENGINE

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## 특징
> * 웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
> * 멀티 OS(Windows, Android, IOS), 멀티 브라우저(IE11, Windows Edge, FireFox, Chrome, Safari), No-Plugin 지원
> * 3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
> * 거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
> * 다양한 도시계획 시뮬레이션 및 분석 기능 제공
> * 공간정보 오픈플랫폼(V World) 데이터 서비스 가능

## 기능
> * 대규모 3차원 공간데이터 로딩 및 사용자 시점에 따른 레벨 별 출력 기능
> * 다양한 형태의 3차원 데이터 조망과 자유로운 시야 컨트롤 기능
> * 좌표계 설정변환, 레이어 제어 등 편리한 공간 객체 관리 기능
> * 행성규모의 대용량 지형 및 위성, 항공영상 지형 Mapping 지원
> * 가시권, 일조권, 스카이라인 사선분석 등 다양한 분석 기능 제공
> * 3DS, ASE, OBJ 등 다양한 3차원 모델링 파일 불러오기 기능
> * KML, KMZ, GML 등 표준 포맷 지원
> * 지구본 단위 V World 서비스에 다양한 MashUP 기능 제공

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
>
> ### 2022년 3월 25일
> 아래 클래스 API는 더 이상 활용되지 않는 관계로 2022년 04월 25일 업데이트 이후 사용이 불가함을 알려드립니다.
> * 클래스 JSLibraryObject 전 API
> * 클래스 JSBuildingManager 전 API

## 업데이트
> ### 2022년 4월 15일
> * Real3D 3DS export 시 메시 방향 지정 오류 수정
> ### 2022년 4월 21일
> * Real3D 객체 페이스 색상 가시화 모듈 수정
> ### 2022년 4월 21일
> * JSLineString 좌표 반환 기능 오류 수정
