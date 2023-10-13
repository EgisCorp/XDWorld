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

### 1.54.1 Hotfix (2023/10/13)
#### 1. WMS, WMTS 이미지 투명도 설정 오류 수정
 * 이미지 일부 영역에 투명 값이 정상적으로 설정되지 않는 부분을 수정하였습니다.
#### 2. JSPolygon loadTexture API 콜백 프로퍼티 추가 ([이슈 #336](https://github.com/EgisCorp/XDWorld/issues/336))
 * Fire_EventTextureLoadComplete 이벤트 처리 대신 loadTexture API에 이미지 로드 콜백을 받을 수 있도록 수정되었습니다.
    ``` javascript
    polygon.loadTexture("polygon_rtt_texture", {
        url : "./data/polygon_rtt_texture", 
        callback : function(e) {
            console.log(e);
        }
    });
    ```
 * 기존 콜백 처리가 없는 loadTexture API도 혼용 가능합니다.
    ``` javascript
    polygon.loadTexture("polygon_rtt_texture", "./data/polygon_rtt_texture");
    ```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
