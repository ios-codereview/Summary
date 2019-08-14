# 코드리뷰

실력은 부족하지만 코드리뷰해드려도 될까요..?

소중히 작성하신 코드를 **무료**로 리뷰해 드립니다. 

## 코드 리뷰 이후? 
개발하면서 질문이 있다면 같이 고민해 드립니다.
> 시간이 부족하거나 제 지식의 짧음으로 같이 고민을 할 수 없는 상황이 발생할 수 있습니다.

## 참여 방법 
https://open.kakao.com/o/sl4DKQyb 

1. 카카오 1:1 대화 참여
2. 코드리뷰 의뢰 
3. 코드리뷰를 위한 Branch 를 생성 
4. 코드리뷰를 받길 원하는 Github 주소 전달해 주시면 됩니다.

## 선택 옵션
* 매운맛: 아키텍처, 디자인패턴의 기회가 있는지 살펴봅니다.
* 중간맛: 제가 선호하는 코드 의견을 살짝 포함합니다.
* 순한맛: 기본적인 사항들을 다룹니다.

> 가능하면 라이브러리보단 3~4개의 화면을 가진 어플리케이션이 좋습니다.

## 주의
면접을 위한 사전 과제는 도와드릴 수 없습니다. 

면접이 종료된 후 신청하실 수 있습니다. 

### 같이 성장할 수 있는 기회가 되었으면 좋겠습니다.

## 정보 공개 동의
코드 리뷰의 결과를 공개하는데 동의가 필요합니다.
### 필수 
* Source Code, Comments





## 1. 익명님 중간맛
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

## 2. Jae-Eun님 [코드리뷰](https://github.com/ios-codereview/Toonie) 매운맛
20건의 Comment 를 드렸습니다.
### Comments
* SwiftLint를 적용하였습니다.
* 가능하면 네트워크 통신 Service는 Tesable 하도록 의존성 주입을 받아야 합니다.
* 네트워크 통신을 하는 동안 사용자에게 로딩을 보여주고 로딩이 보여지는 동안 사용자 이벤트가 동작하지 않아야 합니다.
* 부모 ViewController 에 따라 자식 ViewController 는 종료되는 것이 좋습니다.

`self.navigationController?.popViewController(animated: true)`  
* extension 함수를 활용하는 것이 좋습니다.

`func makeRandomList<T>(_ list: [T], number: Int) -> [T]`
* UserDefaults 의 Key 가 String literal 로 설정하지 않는 것이 좋습니다.

`UserDefaults.standard.integer(forKey: "appStartCount")`

* ScreenUtils class 에서 resolution을 관리하는 것이 좋습니다.
```
static let deviceWidth: CGFloat  = 375
static let deviceHeight: CGFloat = 812
```
* 에러를 흘러보내는 Case가 있었습니다.
```
case .networkError(let error):
    print(error)
case .networkFail:
    print("ToonofTag Network Fail")
```
* encode 하지 않는 객체가 Codable protocol을 따르고 있었습니다.

`struct ChkToonieUpdate: Codable`
* API Path를 지정할 때 Builder 패턴을 사용하면 좋습니다.
```
static let chkToonieUpdate = {
        return baseURL + "/version"
    }()
```
* UICollectionView 에서 row 보단 item이 적절합니다.
`keywords[indexPath.row]`
* Cell에서 직접 속성을 가지는 것 보다 데이터모델을 만드는 것이 좋습니다.

`cell.cellStatus = false`
* 네트워크나 io 작업은 viewWillAppear 보단 viewDidAppear 에서 하는 것이 좋습니다.
```
 override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        setKeywordValue()
        setSelectedKeywordValue()
    }
```

### 배운점
앱의 디자인도 상당히 우수하며 3분이서 같이 개발에 참여하면서 코드의 스타일이 일관성이 있어서 협업이 정말 좋았다라는 걸 느꼈습니다.

잘 만든 앱을 리뷰하게 되어서 영광입니다.
