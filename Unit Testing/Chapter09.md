# 목 처리에 대한 모범 사례
## 목의 가치 극대화 하기

- 시스템 끝에서 상호작용 검증하기
  - 목으로 만드는 객체는 시스템 끝에 있는 객체일수록 좋다.
  - 시스템 끝부분을 목으로 처리하면 그만큼 더 많은 코드를 테스트 할 수 있게되며 따라서 회귀방지와 리펙터링 내성이 좋아진다.
    - 비관리 프로세스 외부 의존성에 관한 코드를 끝으로 몰았으므로..
- 목을 스파이로 대체하기
  - 스파이는 목과 같은 목적을 달성하지만 수동으로 작성한 테스트 대역이다.
  - 시스템 끝에 있는 클래스의 경우 스파이가 목보다 낫다.
  - 검증단계에서 코드를 재사용해 테스트 크기를 줄이고 가독성을 향상시킬 수 있다.
  - 플루언트 인터페이스 형식으로 가독성을 높히며 목보다 더욱 간단항 방법으로 테스트 검증문을 재사용하는 것이 가능하다.

- 목은 통합테스트에서만 사용하기
 - 이전에 설명한대로 단위테스트에서 목을 사용하지 않음.
- 테스트당 목이 하나일 필요는 없다
  - 동작 단위를 검증하는데 필요한 목의 수는 제한될 수 있는것이 아니다.
- 호출 횟수 검증하기
  - 시스템은 프로세스 외부 의존성에 대해서 예상치 못함 메세지를 생성해서는 안되며 예상 되는 메세지를 생략해서도 안된다. 따라서 호출 횟수를 검증해야한다.
- 보유 타입만 목으로 처리하기
  - 서드파티 라이브러리를 그대로 사용하지 말고 우리의 도메인에 맞게 어뎁터를 작성하여 서드파티 라이브러리의 사용방법을 정의해야한다.
    - 서드파티의 작동방식에 깊이 이해하지 못하는 경우가 많다.
    - 서드파티 라이브러리가 인터페이스를 재공하더라도 해당 인터페이스로 목을 만드는 것은 목으로 만든 동작이 라이브러리의 동작과 일치하는지 확인해야하므로 위험함.
    - 서드파티 코드의 기술 세부사항까지는 중요한 사항이 아니므로 애플리케이션이 사용하고자 하는 관점에서 라이브러리와의 관계를 정의해야한다.

   - 따라서 다음과 같은 지침이다.
     - 라이브러리의 복잡성을 추상화하고
     - 라이브러리에서 필요한 기능만 노출하며
     - 프로젝트의 도메인언어를 통해 동작을 수행할 수 있어야한다.

## 개인적인 정리
 - 결과적으로 하위 호환성이 유지되는 비관리 프로세스 외부 의존성의 기능을 코드의 끝부분으로 몰아서 테스트의 리팩터링 내성과 회귀방지를 높히자는 이야기가 핵심.
