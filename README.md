[![EgisLogo](https://user-images.githubusercontent.com/82925313/160987075-ce7eada9-91ca-4b72-beb6-396e142f90a2.png)](http://www.egiskorea.com/)

### Developers - http://www.egiskorea.com/
### Documentation
  * [Korean] https://egiscorp.gitbook.io/xdworld-webgl-manual
  * [English] https://egiscorp.gitbook.io/xdworld_global_manual
### Demos & Sandbox - https://sandbox.egiscloud.com

# Introduction

> XDWORLD ENGINE, a 3D GIS engine based on WebGL

![pd_3_img](https://user-images.githubusercontent.com/82925313/160986727-f473c308-7881-4342-8c08-e31566d93a3b.png)

## Features
-   웹 표준 기술 HTML5, WebGL 기반 3D 렌더링 지원
-   멀티 OS, 브라우저, No-Plugin 지원
-   3차원 공간데이터 웹 개발자를 위한 다양한 Javascript 웹 API 지원
-   거리, 면적 체적 계산 등 기본적인 3차원 분석기능 제공
-   다양한 도시계획 시뮬레이션 및 분석 기능 제공
-   공간정보 오픈플랫폼(V World) 데이터 서비스 가능
<br>

-   Supports 3D rendering based on web standard technologies HTML5 and WebGL
-   Multi OS, browser, and No-Plugin support
-   Provides a variety of JavaScript web APIs for 3D spatial data web developers
-   Offers basic 3D analysis functions such as distance, area, and volume calculations
-   Provides various urban planning simulation and analysis features
-   Capable of spatial information open platform (V World) data services

## Fields

-   GIS, UIS, LBS, 시설물관리, 조감도, 입지분석, 지형분석, 도시계획, 건축현장관리, 농지관리 등
(GIS, Urban Information Systems, Location-Based Services, Facility Management, Perspective Views, Site Analysis, Terrain Analysis, Urban Planning, Construction Site Management, and Agricultural Land Management.)

## Update

- 정기 배포 날짜는 **매월 첫째 주 월요일**입니다. 배포 일정이 변경될 경우, 현재 섹션에서 변동 사항을 확인하실 수 있습니다.


### 2.23.0 (2026/02/02)
#### 1. JSPolygon `loadFile` projectioncode 타입 변경
  * projectioncode  : "EPSG:5186"
  * 기존 숫자코드는 가독성이 떨어져 EPSG 코드를 입력할 수 있도록 변경하였습니다.

#### 2. 오브젝트레이어 POI 원근 스타일 설정 추가 
   - JSLayerList::createObjectLayer로 생성한 레이어 한정
   - JSLayer : setLayerStyle({object}) 추가
   - POI가 카메라와 표출 거리에 따른 크기 및 투명도 설정
  ```
 let option = {
         "poi" : {
            "scaleable" : {             // 거리별 가변 크기 적용
                "activate" : true,      // 동작 설정
                "range" : {
                    "min" : 1000,       // 최소 구간 (보다 가까우면 원본 POI 표현)
                    "max" : 3000        // 최대 구간 (보다 멀면 최소 픽셀 POI 표현)
                }, 
                "minPixel" : {          // 아이콘 최소 픽셀 크기 설정 (아이콘 크기에서 x,y중 작은쪽 크기가 최소 크기보다 작으면 해당 크기로 고정)
                    "x" : 4,         
                    "y" : 16
                },
                "tiltRange" : {             // 각도에 따른 크기 왜곡 추가
                    "activate" : true,      // 왜곡 사용
                    "minAngle" : 60,        // 최소 왜곡 각도 (이하 각도에서는 기존 배율적용)
                    "maxAngle" : 80         // 최대 왜곡 각도 (이상 각도에서는 원본 크기로 표현)
                }
            },
            "fadeable" : {              // 거리별 투명도 적용
                "activate" : true,      // 동작 설정
                "range" : {
                    "min" : 3000,       // 최소 구간 (보다 가까우면 불투명)
                    "max" : 5000        // 최대 구간 (보다 멀면 최소 알파값 적용)
                },
                "minAlpha" : 0.2,        // 최소 투명도값 1>minAlpha>0 ( 이보다 더 투명해지지 않음 )
                "tiltRange" : {             // 각도에 따른 투명도 왜곡 추가
                    "activate" : true,      // 왜곡 사용
                    "minAngle" : 60,        // 최소 왜곡 각도 (이하 각도에서는 기존 배율적용)
                    "maxAngle" : 80         // 최대 왜곡 각도 (이상 각도에서는 원본 크기로 표현)
                }
            }
        }
    };
```

#### 기본형태 
<img width="674" height="754" alt="image" src="https://github.com/user-attachments/assets/c768699e-3dd0-4547-8476-3d1114b5e81c" />

#### 크기 가변형태
<img width="840" height="638" alt="image" src="https://github.com/user-attachments/assets/2f2b4cd4-e7b5-4e97-b37e-41bf2785fbf1" />

#### 투명도 가변형태
<img width="801" height="789" alt="image" src="https://github.com/user-attachments/assets/4e8216a8-659c-4766-b304-7c55708381f4" />

#### 혼합사용 형태
<img width="1027" height="786" alt="image" src="https://github.com/user-attachments/assets/2a38301f-bf2d-4c00-803a-e8ba61d0a00d" />

#### 각도 왜곡 미적용 (Tilt와 관계 없이 거리별 크기 적용)
<img width="776" height="810" alt="image" src="https://github.com/user-attachments/assets/cc4a999d-cb1a-4070-a3e4-d5f3a5467295" />

#### 각도 왜곡 적용 (지정된 Tilt각 이상에서는 원본 크기로 적용 왜곡)
<img width="677" height="914" alt="image" src="https://github.com/user-attachments/assets/ae0edb6f-0e41-4c44-9c42-138cd6519061" />

#### 3. JSPoint POI 자동 높이 조절 기능 property 추가
  ```javascript
  var point = Module.createPoint("POI");
  point.autoHeight  = true;
  ```

#### 4. JSPolygon 정렬 유지되도록 API 수정
* JSPolygon의 setScale, move API 실행 시 윗정렬, 바닥정렬이 유지되도록 기능이 개선되었습니다.

### 2.23.0 (2026/02/02)
#### 1. Change JSPolygon `loadFile` projection code type

* `projectioncode` : `"EPSG:5186"`
* The existing numeric code was hard to read, so it has been changed to allow EPSG codes to be entered directly.

#### 2. Add perspective-based POI style settings for Object Layers

* Applies only to layers created via `JSLayerList::createObjectLayer`
* Add `JSLayer : setLayerStyle({object})`
* Configure POI size and transparency based on camera distance and view angle

```javascript
let option = {
    "poi": {
        "scaleable": {                 // Distance-based scalable size
            "activate": true,          // Enable/disable
            "range": {
                "min": 1000,           // Minimum range (closer than this → original POI size)
                "max": 3000            // Maximum range (farther than this → minimum pixel POI size)
            },
            "minPixel": {              // Minimum icon pixel size
                                       // (If the smaller of x or y is less than this, it is fixed to this size)
                "x": 4,
                "y": 16
            },
            "tiltRange": {             // Additional size distortion based on camera tilt
                "activate": true,      // Enable distortion
                "minAngle": 60,        // Minimum distortion angle
                                       // (Below this angle, normal scaling is applied)
                "maxAngle": 80         // Maximum distortion angle
                                       // (Above this angle, original size is used)
            }
        },
        "fadeable": {                  // Distance-based transparency
            "activate": true,          // Enable/disable
            "range": {
                "min": 3000,           // Minimum range (closer than this → fully opaque)
                "max": 5000            // Maximum range (farther than this → minimum alpha applied)
            },
            "minAlpha": 0.2,           // Minimum alpha value (1 > minAlpha > 0)
                                       // (Will not become more transparent than this)
            "tiltRange": {             // Additional transparency distortion based on camera tilt
                "activate": true,      // Enable distortion
                "minAngle": 60,        // Minimum distortion angle
                                       // (Below this angle, normal alpha is applied)
                "maxAngle": 80         // Maximum distortion angle
                                       // (Above this angle, original alpha is used)
            }
        }
    }
};
```

#### Default appearance
<img width="674" height="754" alt="image" src="https://github.com/user-attachments/assets/c2bb0d0c-f4cd-422e-b77e-8462baaa0544" />

#### Scalable size appearance
<img width="840" height="638" alt="image" src="https://github.com/user-attachments/assets/6616162b-3454-4fc2-82c4-ebfba2d4c056" />

#### Variable transparency appearance
<img width="801" height="789" alt="image" src="https://github.com/user-attachments/assets/ffffbc72-a7ba-4da1-918d-0b1c90cef97c" />

#### Combined usage (size + transparency)
<img width="1027" height="786" alt="image" src="https://github.com/user-attachments/assets/0b64b779-a4b9-45ba-a8e9-f8b7cbe66708" />

#### Tilt distortion disabled (Size varies only by distance, regardless of tilt angle)
<img width="776" height="810" alt="image" src="https://github.com/user-attachments/assets/18f29dd1-bf22-4814-bed1-e56e5c2ce957" />

#### Tilt distortion enabled (Above the specified tilt angle, POIs are rendered at their original size)
<img width="677" height="914" alt="image" src="https://github.com/user-attachments/assets/1535d43c-6994-4d27-a13e-cde04e6a2db3" />

#### 3. Add automatic height adjustment property for JSPoint POIs

```javascript
var point = Module.createPoint("POI");
point.autoHeight = true;
```

---
#### 4. Keep JSPolygon alignment when updating transform APIs
* The JSPolygon **setScale** and **move** APIs have been improved so that **top alignment** and **bottom (ground) alignment** are preserved when they are executed.

## [Previous Version Update](https://egiscorp.gitbook.io/xdworld-webgl-manual/release)

## Running XDWorld with Vue.js
  * https://egiscloud.com/siteData/vue/index.html
