# Redux-saga

## takeEvery

- 모든 요청에 대해 실행

## takeLastest

- 같은 요청이 들어올 경우 이전 요청을 취소하고 마지막 요청만 실행
- 로그인 버튼 같이 요청에 대해 1회만 실행하기를 원할 때 유효한 방법

## call

- 동기 호출
- 서버에 호출을 보내고 그 호출에 대한 응답을 받을 때까지 대기
- 순서를 지켜서 실행해야 하는 경우

## fork

- 비동기 호출
- 서버에 호출을 보내고 즉시 다음 명령 실행
- 로깅 따위의 순서가 상관없는 경우에 사용
- all에 묶을 경우 fork 사용

## put

- dispatch와 비슷
- 다음 동작을 넣어주는 것
  - ex) LOG_IN -> LOG_IN_SUCCESS(FAILURE)

## delay

- 다음 동작을 지연시키는 것

## all

- 동시에 실행 (watch 함수를 넣으면 됨)

## race

## cancel

## select

## throttle

## debounce
