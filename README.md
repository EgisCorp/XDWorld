[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual
### Demos & Sandbox - https://sandbox.egiscloud.com
### Demos & Sandbox (beta) : https://sandbox.egiscloud.com/code/main.do?id=start&engine=beta&worker=true

# Introduction

> WebGL 기반 3D GIS 엔진 XDWORLD ENGINE

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## 특징

-   웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
-   멀티 OS, 브라우저, No-Plugin 지원
-   3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
-   거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
-   다양한 도시계획 시뮬레이션 및 분석 기능 제공
-   공간정보 오픈플랫폼(V World) 데이터 서비스 가능

## 적용분야

-   GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등

## 최근 업데이트

### 1.58.0 (2024/1/26)

#### 1.  JSProj 클래스 제공
  * CRS(Projection)로 설정된 여러 좌표에 해당되는 위치값을 특정 CRS(Projection)로 변환 하는 기능을 추가 하였습니다.
  * 상세 관련내용은 메뉴얼 [JSProj](https://egiscorp.gitbook.io/xdworld-webgl-manual/introduce-1/etc/jsproj) 참조 부탁드립니다.

#### 2. 월드 배경 색상 적용
  * JSOption에 backgroundColor : { JSColor } 속성을 통한 월드 색상 변경 적용이 추가되었습니다.

#### 3. 건물 카메라 확대 시 거리 조절 [이슈 #378](https://github.com/EgisCorp/XDWorld/issues/378)
  * Class JSCamera 구성요소 추가
    * 변수항목
      * collision_type(type boolean) : 휠 이벤트에서 카메라와 선택지점 충돌 유무를 설정합니다.
      * collision_distance(type number) : 휠 이벤트에서 카메라와 선택지점(마우스 이벤트 지점) 보간 거리를 설정합니다.

 ``` javascript
var camera = Module.getViewCamera();
camera.collision_type = true;
camera.collision_distance = 20;
```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
