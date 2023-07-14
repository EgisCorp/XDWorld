[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/

### Documentation - https://egiscorp.gitbook.io/xdworld-webgl-manual

### Demos & Sandbox - http://sandbox.dtwincloud.com

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

### 1.52.1 Hotfix (2023/7/14)

#### 1. 엔진 내 마우스 버튼 눌림 상태 프로퍼티가 추가되었습니다.
 * JSControl 내 마우스 왼쪽 버튼 눌림(mouseLeftButtonDown), 오른쪽 버튼 눌림(mouseRightButtonDown) 프로퍼티가 추가되었습니다.
   ``` javascript
   console.log(Module.getControl().mouseLeftButtonDown);
   console.log(Module.getControl().mouseRightButtonDown);
   ```

#### 2. Mobile Touch Rotate Event tilt 제한 기능을 수정하였습니다.
 * JSCamera.setLimitTilt("입력값") 설정 후 모바일 touch rotate event시 제한이 안되는 문제를 수정하였습니다.

#### 3. 측면 두께를 가진 Polygon 생성 기능을 추가 하였습니다. 
 * 고도를 기준 축으로 측면으로 두께가 있는 JSColorPolygon 생성 기능을 추가하였습니다.
 * API : JSColorPolygon.createbyJson(parameter);
 * 샘플코드
 ``` javascript
var polygon = Module.createColorPolygon("GRADATION_POLYGON");
let parameter = {
    coordinates: {
        coordinate: vertices,    // geometry 경위도좌표 목록
        index: indices,              // geometry 가시화 인덱스 설정
    },
    color: colors,              // 정점 색상 설정
    thickness: 0,               // 두께 설정(m 단위)
};
polygon.createbyJson(parameter);
```

#### 3. JSColorPolygon 경위도 좌표 반환 기능을 추가 하였습니다.
 * JSColorPolygon을 구성하는 geometry 경위도 좌표 목록을 반환하는 기능
 * API : JSColorPolygon.toLonlatArray();

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
