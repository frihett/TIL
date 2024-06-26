# Unit test

## 목적
-  테스트를 통한 품질 향상

## 테스트의 장점
- 장애에 관한 신속한 피드백
- 개발 주기에서 조기 장애 감지
- 회귀에 신경 쓸 필요 없이 코드를 최적화할 수 있도록 하는 더 안전한 코드 리펙토링
- 기술적 문제를 최소화하는 안정적인 개발 속도

## 테스트의 종류
테스트의 종류로는 크게 세 가지로 나뉩니다.
- 수동 테스트 : 인간이 하는 테스트
- **단위 테스트** : 1개의 함수(단위) 테스트
- 통합 테스트 : 여러 개의 연관된 클래스나 함수를 함께 테스트 (UI test, Integration test)

## 테스트 방법론
**화이트박스 테스트**
- 내부 구조와 동작에 중점을 두고 테스트하는 방법
- 코드의 내부 로직, 제어 흐름, 데이터 흐름 등을 이해하고 검증하는 데에 사용
- 테스트 케이스를 설계할 때 코드의 특정 부분을 직접 확인
- 주요 기법으로는 구문 검사, 경로 검사, 조건/분기 검사 등이 있음

**블랙박스 테스트**
- 소프트웨어의 내부 구조를 무시하고 기능을 테스트하는 방법
- 시스템이 어떻게 동작하는지에 대한 내부 정보를 알 필요 없이 사용자 관점에서 테스트
- 테스트 케이스는 입력 값과 예상 출력 값에 기반하여 설계
- 요구 사항을 충족하는지 확인하고, 시스템의 기능적 및 비기능적 요구 사항을 테스트
- 주요 기법으로는 등가 분할, 경계 값 분석, 상태 전이 테스트 등이 있음

### 단위 테스트(Unit Test)란?
> 특정 모듈이 의도한 대로 잘 작동하는가를 테스트하는 가장 작은 단위의 테스트

### 테스트 코드 작성법
1. test 디렉토리에 **{기존파일}_test.dart** 형식으로 파일 생성
2. test 패키지를 import 후 test() 함수 사용
```dart
import 'package:test/test.dart';

void main() {
  test('Test', () {
    // 테스트 내용
  });
}
```
3. given > when > then 기법을 사용하고 expect() 함수로 검증
```dart
test('Test', () {
  // given (준비)
  final value = Value('value', '값');
  final expected = 'value';
  
  // when (실행)
  final firstValue = value.getFirst();
  
  // then (검증)
  expect(firstValue == expected, true);
}
```

## Mock
이런 단위 테스트도 불편함이 발생하는데,
라이브 웹 서비스나 데이터베이스에서 데이터를 가져오는 경우가 그렇습니다.
예기치 않은 오류가 발생하여 테스트가 지연되거나 정상적으로 진행이 안 될 수 있습니다.
따라서 이러한 경우에는 가상 더미 데이터를 활용할 수 있습니다.
이렇게 테스트가 가능하게 해주는 객체를 Mock 객체라고 합니다.
