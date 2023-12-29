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
### 1.57.0 (2023/12/29)
#### 1.  최근 화면 갱신 시간 반환 프로퍼티 추가
  * JSMap 프로퍼티를 통해 화면이 최근 갱신 된 시각을 년/월/일/시/초 단위로 반환하는 프로퍼티가 추가되었습니다.
    ``` javascript
    var time = Module.getMap().lastRenderTime;
    ```
    ![image](https://github.com/EgisCorp/XDWorld/assets/82925313/757bf64f-6a5e-40c7-b230-a8a8add6de49)


#### 2. 2D 바 그래프 값 가시화 설정 프로퍼티가 추가 : [이슈 #365](https://github.com/EgisCorp/XDWorld/issues/365)
  * 2D 바 그래프 값(컬럼 단위, 총 단위) 가시화 설정 프로퍼티가 추가되었습니다.
  * 컬럼 단위 값 가시화 설정
    ``` javascript
    graph.columnValueVisible = false;
    ```
  * 총 단위 값 가시화 설정
    ``` javascript
    graph.totalColumnValueVisible = false;
    ```

#### 3. 1인칭 카메라 이동 시 가시범위 조정 : [이슈 #363](https://github.com/EgisCorp/XDWorld/issues/363)
  * 1인칭 카메라 설정 시 오브젝트 최소 가시범위를 낮추어 카메라 앞 지형이 컬링되는 현상을 제거하였습니다.


## [이전 버전 업데이트](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)
