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
### 1.55.1 (hotfix)
#### 1. [#341 이슈](https://github.com/EgisCorp/XDWorld/issues/341) 해결

### 1.55.0 (2023/10/27)
#### 1. JSPolygon 내 픽셀 기반 텍스쳐 로드 기능이 추가되었습니다.
 * 기존 URL로 데이터를 로드하는 loadTexture API에 픽셀 데이터를 바로 적용할 수 있도록 기능이 업데이트 되었습니다.
 * 네트워크를 통해 데이터를 로드하지 않으므로 API 실행 후 바로 setFaceTexture API를 통해 텍스쳐를 적용할 수 있습니다.
 ``` javascript
 function setFaceTextureByPixelColors(_polygon, _faceIndex) {

     // 이미지를 그릴 캔버스 생성
     var canvas = document.createElement("canvas");
     canvas.width = 128;
     canvas.height = 128;

     var context = canvas .getContext("2d");

     (... context를 활용하여 canvas 이미지 그리기...)

     // canvas에 그려진 픽셀 데이터 반환
     
     // JSPolygon의 텍스쳐 리스트로 저장
     _polygon.loadTexture("텍스쳐이름", {
        width : canvas.width,
        height : canvas.height,
        pixels : context.getImageData(0, 0, canvas.width, canvas.height).data
    });
    
    // JSPolygon 첫번째 Face에 텍스쳐 지정
    _polygon.setFaceTexture(0, "텍스쳐이름");
 }
```

## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
