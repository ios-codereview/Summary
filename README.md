# 코드리뷰

소중히 작성하신 코드를 **무료**로 리뷰해 드립니다. 

가능하면 라이브러리보단 3~4개의 화면을 가진 어플리케이션이 좋습니다.

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


## 참여 후기를 알려주세요.
링크를 통해 설문지를 작성해 주세요.

## 주의
면접을 위한 사전 과제는 도와드릴 수 없습니다. 

면접이 종료된 후 신청하실 수 있습니다. 

## 정보 공개 동의
코드 리뷰의 결과를 공개하는데 동의가 필요합니다.
### 필수 
* Source Code
### 선택
* Comments 
> Default: 비공개

공개를 원하시는 경우 Github Summary에 Comment 내용이 표시됩니다.



## 92pino님 [코드리뷰](https://github.com/ios-codereview/StoreCopy) 매운맛
14건의 Comment 를 드렸습니다. 

[Refactoring] 6건 [사용성] 5건 성능 2건 [이슈] 1건

### Comments
표시하지 않음

### 리뷰 후기
* TableView, CollectionView 두가지 버전의 멋진 앱스토어를 구현하셨습니다. 

## namsoo5님 [코드리뷰](https://github.com/ios-codereview/DanBee_iOS) 매운맛
27건의 Comment 를 드렸습니다. 

[Refactoring] 19건 [사용성] 4건 [이슈] 4건

### Comments
표시하지 않음

### 리뷰 후기
* DanBee 라는 멋진 컨셉으로 혼자 많은 화면을 개발하고 계셨습니다.
사용성 부분과 MVVM 아키텍처를 능숙하게 다루시게 된다면 멋진 앱이 될 것 같습니다.


## applebuddy님 [코드리뷰](https://github.com/ios-codereview/WeatherCopyApp) 매운맛
27건의 Comment 를 드렸습니다. 

[Refactoring] 17건 [사용성] 6건 [경고] 2건 [성능] 2건

### Comments
표시하지 않음

### 리뷰 후기
* 멋진 Nested ScrollView 를 구현하셨습니다. 상당히 까다로운 작업이 많았을 것이라 생각합니다.
멋진 날씨 앱이었습니다!


## onemoonStudio [코드리뷰](https://github.com/ios-codereview/randomImage) 매운맛
20건의 Comment 를 드렸습니다. 

[성능] 3건 [사용성] 5건 [Refactoring] 12건

### Comments

* [성능] async 로 동작하는게 좋지 않을까요?
```
CacheImageManager.downsampledImageQueue.sync(execute: imageTask)
```
* [성능] Image 다운로드 중인 네트워크 작업들을 취소하는것이 좋지 않을까요?
```
func collectionView(_ collectionView: UICollectionView, didEndDisplaying cell: UICollectionViewCell, forItemAt indexPath: IndexPath) {
// 취소
}
```
* [사용성] 하얀색 이미지를 Zoom 하면 Close 버튼이 보여지지 않습니다. (같은 흰색이기 때문에 겹침니다)
```
@IBOutlet weak var closeButton: UIButton! {
        didSet {
            closeButton.addTarget(self, action: #selector(closeImageDetail), for: .touchUpInside)
        }
    }
 ```
* [사용성] 화면을 회전한 경우 제대로 Frame이 설정되지 않습니다.

viewDidLayoutSubviews 에서 layout을 update을 하는건 어떨까요?
``` 
 lazy var imageFrame: CGRect

```
* [Refactoring] Cache와 API에서 Image를 가져오는 것은 Repository 패턴을 사용하는건 어떨까요?

![](https://miro.medium.com/max/1400/1*UDzzNYwInvHg25V_OtWejg.jpeg)

* [Refactroing] 이미지 다운로드의 같은 작업이 이미 실행 중인지 검사도 필요하지 않을까요? (ImageURL은 중복될 수 있습니다)
```
APIManager.downloadImageData(urlString) { (data)
```
* [Refactoring] 이미지 다운로드의 URLSession은 ephemeral 옵션으로 생성하는건 어떨까요?

ephemeral은 캐시, 쿠키 또는 자격 증명에 영구 저장소를 사용하지 않는 세션 구성입니다.

```
URLSession(configuration: .default).dataTask(with: url) { (data, _, error)
```
* [Refactoring] 정확한 기능을 명시하는건 어떨까요?

`ex) centerIfNeeded`
```
 func scrollViewDidZoom(_ scrollView: UIScrollView) {
        ...
        imageView.frame.origin = newImageOrigin
    }
```
* [Refactoring] 유연하게 API를 호출 할 수 있도록 URLRequest 를 Parameter로 전달하는건 어떨까요?

`keyword: String, page: Int` 를 parameter 로 받으면 특정 API 만 사용할 수 있게 됩니다.
범용적으로 쓰기 위해선 URLRequest로 전달하는 것이 좋습니다.
```
func imageItems(request: URLRequest, completion: @escaping (_ imageData: [ImageItem]?, _ error: Error? ) -> Void )
```

### 리뷰 후기
 * 이미지 검색 결과가 TableView 와 CollectionView 두 가지 타입으로 지원하며 Paging 기능도 제공하고 있습니다.
 * 손이 많이 가는 작업들이었으며 훌륭하게 기능을 구현하셨습니다!

> 좋은 리뷰 감사합니다! 리뷰를 받으니 조금 더 명확하게 짜는 습관을 길러야 겠다는 생각이 드네요 ! 😃

## sogih님 [코드리뷰](https://github.com/ios-codereview/github-user-search-ios) 매운맛
15건의 Comment 를 드렸습니다. 

[성능] 1건 [사용성] 1건 [Refactoring] 13건

### Comments
표시하지 않음

### 리뷰 후기
* 개발자가 뛰어나고 일관성있는 애니메이션을 표현하는 것은 어려운 일이라고 생각합니다.
이 부분에 많은 시간과 노력을 투자했을 것이라 생각합니다. 
* 덕분에 사용성이 좋은 애니메이션 효과를 경험하였습니다.

## jinuman님 [코드리뷰](https://github.com/ios-codereview/github-user-search-ios) 매운맛
15건의 Comment 를 드렸습니다. 

__처음 RxSwift, ReactorKit 리뷰를 하게 되었습니다.__

**테스트코드를 작성해 드렸습니다.**

[성능] 2건 [사용성] 9건 [경고] 1건 [Refactoring] 3건

### Comments

* [사용성] 이미지 다운로드 실패했을 경우 Placeholder 이미지를 보여줘야 합니다.
```
if let error = error {
                // Review: [사용성] 이미지 다운로드 실패했을 경우 Placeholder 이미지를 보여줘야 합니다.
                print(error.localizedDescription)
                return
            }
```
* [사용성] fetchUsers 를 실패하면 사용자에게 알려줘야 합니다.
```
 func fetchUsers(with query: String?, page: Int) -> Observable<(repos: [UserItem], nextPage: Int?)> {
        // Review: [사용성] fetchUsers 를 실패하면 사용자에게 알려줘야 합니다.
        let emptyResult: ([UserItem], Int?) = ([], nil)
```

* [사용성] 검색된 결과가 없다면 "검색 결과가 없습니다" View가 보여줘야 합니다.
* [Refactoring] UserItem 은 Service에서 return 하는것이 적절하지 않습니다.
```
class GithubAPI {
        // Review: [Refactoring] UserItem 은 Service에서 return 하는것이 적절하지 않습니다.
        // 순전히 Github Response 데이터를 return 하는 것이 좋습니다.
        // ViewModel 에서 Mapping 작업을 해야 합니다.
	func fetchUsers(with query: String?, page: Int) -> Observable<(repos: [UserItem], nextPage: Int?)>
}
```
* [성능] NextPage를 2번 가지고 오면 총 7번의 연산이 들어갑니다.
```
func testUserItemPaging() {
        // 페이징 동작이 잘 동작하는 지 검증
        let expect = [
            [Fixture.UserItems.sampleUserItems.shuffled().first!],
            [Fixture.UserItems.sampleUserItems.shuffled().first!],
            [Fixture.UserItems.sampleUserItems.shuffled().first!]
        ]
        reset(api)
        api.setUserItemsPaging(expect)

        let rxExpect = RxExpect()
        rxExpect.retain(reactor)

        rxExpect.input(reactor.action, [
                .next(0, .updateQuery("a")),
                .next(10, .loadNextPage),
                .next(20, .loadNextPage),
            ])

        // Reivew: [성능] NextPage를 2번 가지고 오면 총 7번의 연산이 들어갑니다.
        // 3번의 Action을 수행했기 때문에 3번만 Item을 가지고 올 수 있도록 전략이 필요합니다.
        // 배열의 크기가 커지면 치명적인 성능저하가 일어납니다.
        rxExpect.assert(reactor.state.map { $0.userItems }.filterEmpty()) { events in
            XCTAssertEqual(events.count, 7)
            XCTAssertEqual(events[0], .next(0, expect[0]))
            XCTAssertEqual(events[1], .next(10, expect[0]))
            XCTAssertEqual(events[2], .next(10, expect[0] + expect[1]))
            XCTAssertEqual(events[3], .next(10, expect[0] + expect[1]))
            XCTAssertEqual(events[4], .next(20, expect[0] + expect[1]))
            XCTAssertEqual(events[5], .next(20, expect[0] + expect[1] + expect[2]))
            XCTAssertEqual(events[6], .next(20, expect[0] + expect[1] + expect[2]))
        }
    }
```

### 리뷰 후기
* jinuman님의 훌륭한 아키텍처를 경험할 수 있었습니다.
* TestCode를 작성하며 성능의 미치는 영향을 알 수 있어서 좋았습니다.


## Jae-Eun님 [코드리뷰](https://github.com/ios-codereview/Toonie) 매운맛
20건의 Comment 를 드렸습니다.
### Comments
표시하지 않음
### 리뷰 후기
* 앱의 디자인도 상당히 우수하며 3분이서 같이 개발에 참여하면서 코드의 스타일이 일관성이 있어서 협업이 정말 좋았다라는 걸 느꼈습니다.
* 잘 만든 앱을 리뷰하게 되어서 영광입니다.

## 익명님 중간맛
40건의 Comment 를 드렸습니다.
### Comments
비공개
### 리뷰 후기
* 클로저의 순환참조에 대해서 명확하게 알게되었습니다

