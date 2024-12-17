# Context

### Context*(Subject)*
- Application 환경에 관한 전체 정보를 받을 수 있는 추상 클래스
- `Context`는 추상 클래스이기 때문에 구현체가 필요

### ContextWrapper*(Proxy)*
- `Context` 구현체를 래핑하여 `Context` 구현체의 동작을 하도록 위임
    ⇒ `ContextWrapper`는 `Context` 구현체의 메서드를 대신 호출하는 역할 
    ⇒ `Context` 구현체의 변경없이 원하는 기능 및 동작 재정의
    ⇒ `Context` 구현체를 바꾸어도 `Context`를 사용하던 코드 변경 없음

- `ContextWrapper`에서 구현체를 바꾸기 위해 `attachBaseContext()` 사용

### ContextImpl*(Real Subject)*
- `Context`의 기본 구현체로 `ContextWrapper`로 감싸져 있음
- `ContextWrapper`가 래핑하는 구현체가 항상 `ContextImpl`는 아님
- `ContextWrapper` 생성자와 `attachBaseContext()` 메서드에 대입되는 것
- `getBaseContext()`를 통해 `Context`의 인스턴스를 가져옴

### ContextThemeWrapper
- `ContextWrapper`의 서브 클래스로 `Context`의 Theme을 수정하거나 교체
- 테마와 관련된 동작을 `mBase`로 위임하지 않고 멤버변수를 이용
    ⇒ 테마와 관련된 api를 `baseContext`로 위임하지 않고 자신의 Theme 가짐
    
### Component
- 각각 `ContextImpl`를 생성하고 `ContextWrapper`의 메서드를 사용
    ⇒ `getBaseContext()`, `getApplicationContext()`, `getApplication()` 등