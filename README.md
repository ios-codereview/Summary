# 코드리뷰

실력은 부족하지만 코드리뷰해드려도 될까요..?

소중히 작성하신 코드를 **무료**로 리뷰해 드립니다. 

## 코드 리뷰 이후? 
개발하면서 질문이 있다면 같이 고민해 드립니다.
> 시간이 부족하거나 제 지식의 짧음으로 같이 고민을 할 수 없는 상황이 발생할 수 있습니다.
## 선택 옵션
* 매운맛: 아키텍처, 디자인패턴의 기회가 있는지 살펴봅니다.
* 중간맛: 제가 선호하는 코드 의견을 살짝 포함합니다.
* 순한맛: 기본적인 사항들을 다룹니다.

> 가능하면 라이브러리보단 3~4개의 화면을 가진 어플리케이션이 좋습니다.

### 같이 성장할 수 있는 기회가 되었으면 좋겠습니다.

## 정보 공개 동의
코드 리뷰의 결과를 공개하는데 동의가 필요합니다.
### 필수 
* Source Code, Comments





## 1. junyng님
40건의 Comment 를 드렸습니다.

### Comments
1. SwiftLint 를 적용.
2. 데이터 모델을 테이블 셀을 생성하면서 호출하고 있어서 데이터 모델의 분리가 필요.
3. Error를 LocalizedError 따르는 것을 선호 (**중간맛** 효과).
4. 가능하면 ReuseKey 는 String Literal 을 쓰지않는 것이 좋음.
5. 강제 캐스팅 및 에러 처리가 부족한한 부분들.
6. FileManager 를 사용하여 데이터를 저장하는 것보다 DB를 사용하는 것이 적절함.

### 배운점
클로저의 순환참조에 대해서 명확하게 알게되었습니다
