# We Are Javascripters

## 2019-09-30

### Performance Timing API (okamuuu)

### TypeSciprt로 VSCode의 확장기능을 만든 이야기 (kuromoka)

- CircleCI 빌드 결과를 스테이터바에 표시하는 기능
- Code Generator
  - npm install -g yo generator-code
  - yo code
- VSCode의 상단 리스트형 UI는 Quick Pick

### TypeScript에 대한 형태 레벨 바리에이션 (y_taka_23) \*\*\*

- 유령형 Phantom Types
  - 형태에 파라미터를가 붙은 형태를 만듬
- 자세한 내용은 카메라로 사진 촬영했음

### Vue UI가 상상이상으로 편리했던 것을 공유하고 싶다.

- Vue CLI로 제공되고있는 프로젝트 관리 툴
- Vue-Cli 버전 3부터 제공 (@vue/cli)
- CLI는 뒤로가기가 안되지만 가능
- 플러그인의 관리가 쉬움

### Take care to invalidate Client Side Storage (kogai)

- PWA의 구성요소로서 Client Side Storage
  - All app URLs load while offline
  - First load fast even on 3G
  - 문제점
    - 블로그를 갱신해도 얼마간은 최신 컨텐츠가 반영되지 않음
    - unregister 되는 타이밍에 컨텐츠가 없어짐
  - Store를 로컬에 보전하는 어플리케이션
    - 문제점
      - 로컬 스토리지에는 버전별 관리가 되지 않음
      - 유저가 어떤 순서로 어떤 버전을 사용하는지 알 수 없음
  - 정리
    - 매력적인 기술
    - 운영측에 권한이 없는 스토리지 기술

### React-Spring으로 리치한 애니메이션 \*\*\*

- 복잡한 애니메이션을 선언적으로 실행할 수 있음
- 시간 베이스의 애니메이션이 아님
  - mass, tension, friction, precision, velocity
- Hook나 native 플러그인을 부이면 리엔더링을 하지 않음
- 주의점
- left/margin 따위를 사용하면 CPU에 의해 계산이 발생함 (무거워짐)
  - will-change로 프로퍼티를 지정하면 어느정도 GPU를 사용하여 빨라짐
  - xx3D이외에는 전부 CPU를 사용함.
    - 수치계산에 있어서 GPU와 비교하면 빠르지 않음
    - 애니메이션은 GPU를 의식해서 개발할 것
- React-Konva라는 라이브러리로 Canvas의 구축이 가능함
  - Hooks가 아직 적용되지 않음

## Streams API (chikoshi)

- 브라우저가 가지고 있는 API
- fetch는 response object가 돌아옴 (stream object)
- 다운로드를 하면서 컴파일 하는게 가능
- 다운로드 후에 컴파일 하는건 어려움
- wasm는 섹션(파츠)로 이루어져있어서 조금씩 읽으면서 컴파일 가능함
- ReadableStream
- WritableStream
- TransformStream
  - Readable과 Writable 사이에서 변환하는 역활
