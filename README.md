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

### 1.54.0 (2023/9/26)

#### 1. 대기 노을 효과
 * 지정한 일출, 일물 시간에 따라 대기 색상이 변경 되도록 API가 추가되었습니다.
 * API
   * JSOption.setAtmosphericSunriseTime(시간, 분);
   * JSOption.setAtmosphericSunsetTime(시간, 분);
   * JSOption.setAtmosphericTime(시간, 분);
 * 샘플코드
    ```javascript
    // 일출 시간 설정
    Module.getOption().setAtmosphericSunriseTime(6, 30);
    ```
    ```javascript
    // 일몰 시간 설정
    Module.getOption().setAtmosphericSunsetTime(19, 0);
    ```
    ```javascript
    // 대기 시간 설정
    Module.getOption().setAtmosphericTime(12, 0);
    ```

#### 2. 하이브리드 투명도 편집 기능 추가
 * JSLayer에 투명값 조절 API가 수정되었습니다.
 * API : JSLayer.setAlpha(parameter);
 * 샘플코드
    ```javascript
    let layerList = new Module.JSLayerList(false);
	var layer = layerList.nameAtLayer("layername");
	layer.setAlpha(180);
    ```
	
#### 3. WMTS 예외처리
 * 타일링에 따른 WMTS 예외처리가 추가되었습니다.

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
