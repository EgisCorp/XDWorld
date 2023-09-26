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

### 1.53.3 (2023/9/12)
 * [이슈 321](https://github.com/EgisCorp/XDWorld/issues/321) 오류 수정

### 1.53.2 (2023/9/12)

#### 1. 구 폴리곤 생성 API 추가 [이슈 #322](https://github.com/EgisCorp/XDWorld/issues/322)
 * JSPolygon에 구체 폴리곤을 생성하는 API가 추가되었습니다.
 * API : JSPolygon.setSphere(parameter);
 * 샘플코드
    ```javascript
    var polygon = Module.createPolygon("GRADATION_POLYGON");
    let parameter = {
        position: new Module.JSVector3D(lon, lat, alt),    // 경도, 위도, 고도 좌표
        color: new Module.JSColor(255, 0, 255, 0),          // 구 표현색상 default : JSColor(255, 0, 255, 0)
        radius: 40,                                                             // 구 반지름 설정(m 단위)  default : 10
        segment: 50,                                                         // 구 정밀도 설정   default : 30
    };
    polygon.setSphere(parameter);
    ```

#### 2. 폴리곤 깊이 버퍼 on/off 프로퍼티 추가
 * JSPolygon에 깊어 버퍼 테스트를 on/off 할 수 있도록 bool 타입 프로퍼티 'zBufferOff'가 추가되었습니다.
 * 디폴트 값은 false 입니다.
 * 샘플코드
    ```javascript
    polygon.zBufferOff = true;
    ```
    
#### 3. PNG 타일맵 레이어 투명도 조절 기능 추가  [이슈 #321](https://github.com/EgisCorp/XDWorld/issues/321)
 * JSLayer의 setAlpha API의 하이브리드 투명값 조절 기능이  추가되었습니다.
 * API : JSLayer.setAlpha(parameter);
 * 샘플코드
    ```javascript
    let layerList = new Module.JSLayerList(false);
    var layer = layerList.nameAtLayer("layername");
    layer.setAlpha(180);
    ```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
