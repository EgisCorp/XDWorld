## 1.39.0 업데이트 (2022년 12월 14일)
### [새로 추가 된 API]
* void moveTarget(object options)
  * 지정한 방향으로 타겟 오브젝트를 이동시킵니다. (이슈 https://github.com/EgisCorp/XDWorld/issues/236)
  * Class : JSTraceTarget
  * Parameter
      * options : 오브젝트 이동 방향 (front : 전진, back : 후진, left : 왼쪽, right : 오른쪽, up : 상승, down : 하강)
  * Example
      ``` javascript
          trace.moveTarget({
                 left : 0.1,
                 front : 0.1,
                 up : 0.5
          });
      ``` 
* void unionTargetToTerrain()
  * 오브젝트 위치를 지형과 결합시킵니다. 
  * Class : JSTraceTarget
  
### [기능 개선]
* wmts 하이브리드 로드 오류 수정

### [샌드박스]
* 'DEM 경사 조정' 추가(http://sandbox.dtwincloud.com/code/main.do?id=terrain_slope_rate)
* '카메라 경로 가시화' 추가(http://sandbox.dtwincloud.com/code/main.do?id=camera_move_path_visualize)