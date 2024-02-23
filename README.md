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

### 1.59.0 (2024/2/23)

#### 1. 초기 로딩시 지구본이 검게 표현되는 현상 수정
  * 엔진 로드 직후 지형 이미지가 완전 수신 되지 않아 지구본이 검은색으로 표현 되는 현상을 수정하였습니다.

#### 2. 서버 기반 지형 고도 반환 함수 추가
  * 현재 엔진에서 요청 중인 지형 서버로 DEM 고도 값을 수신하는 API가 추가되었습니다.
  * 서버의 고도 값을 리턴하므로 엔진에 낮은 레벨 지형이 로드 된 상태인 경우, 현재 엔진 지형과 DEM 값이 다를 수 있습니다.
  * 값은 비동기로 반환되므로 콜백 함수를 통해 값을 수신합니다.
  * 입력한 경위도 및 지형 레벨에 대응되는 고도 값이 없거나 서버에 지형 데이터가 없는 경우 null을 반환합니다.
  ``` javascript
  Module.getTerrain().getServerAltitude({
      level : 15,
      positions : [
          new Module.JSVector2D(127.055035334602, 37.48664424515323),
          new Module.JSVector2D(127.05509237777562, 37.48664424515323),
          new Module.JSVector2D(127.05509237777562, 37.48668970070035)
      ]
  }, function (result) {
      console.log(result);
  })

  // 반환 값
  (3) [{…}, {…}, {…}]
  > 0 : {longitude: 127.055035334602, latitude: 37.48664424515323, altitude: 9.70352554321289}
  > 1 : {longitude: 127.05509237777562, latitude: 37.48664424515323, altitude: 9.70939826965332}
  > 2 : {longitude: 127.05509237777562, latitude: 37.48668970070035, altitude: null}    // 고도 값이 없는 경우 null 반환
     length : 3
  ```

#### 3. 점선 라인 생성 오류 추가
  * JSLineString 객체의 점선 속성이 적용되지 않는 현상을 수정하였습니다.

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
