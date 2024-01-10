---

---
### 트위닝 : 두 개 이상의 모습을 자연스럽게 이어주는 기능

---
## 설치 방법
##### 1. 유니티 에셋 스토어
- 유니티 에셋 스토어에서 DOTween 검색 후 설치
- 그 후, Unity 에서 열기 클릭
##### 2. 유니티 안에서
- 유니티에 들어오면 로그인하라고 뜰 것임 (안뜰수도 있음).
- 로그인 하고 Package Manager 뜨면 거기 DOTween이 보일것임.
- 조금 기다리면 로딩바 사라지고 Import/Download 나올건데 다운로드 하고 Import 하면 됨.
- 그 후 DOTween 창이 뜨는데 DOTween Utility Panel을 여는 버튼 클릭
- **거기서 Setup DOTween을 클릭해주면 사용 가능 (매우 중요)**
##### 3. 사용 준비 완료!

---
## 사용법
##### 1. 임포트

```C#
using DG.Tweening;
```

를 써서 임포트한다.

##### 2. 함수
기본적으로 **DO** 함수를 써서 이동시킨다.
기존에 Update 함수에서 프레임단위로 이동을 제어하던 것과는 달리, 이 것을 사용하면 **Start 함수에서 한번 호출하는 것 만으로도 자연스럽게 움직이게 할 수 있다.**

- 기초 함수들 :
```C#
transform.DOMove(Vector3.up, 5); // 지정 방향 (Vector3) 으로 5초간 이동
transform.DOScale(Vector.one * 3, 5); // 5초간 크기 3배 증가
transform.DORotate(Vector3.forward, 5); // 5초간 forward 방향으로 회전

Material mat = GetComponent<MeshRenderer>().material;
mat.DOColor(Color.cyan, 5); // 5초간 색을 청록색으로 변경
```

- UI 트위닝 함수:
``` C#
RectTransform rt = GetComponent<RectTransform>();
rt.DOAnchorPosY(도착지점, 시간);

//트위닝 함수 뒤에 시퀸스 함수로 효과 추가하기
RectTransform rt = GetComponent<RectTransform>();
rt.DOAnchorPosY(도착지점, 시간).SetDelay(1.5f); // 1.5초 딜레이

// 더 효과 넣기
RectTransform rt = GetComponent<RectTransform>();
rt.DOAnchorPosY(-350, 1).SetDelay(1.5f).SetEase(Ease.OutBounce); // 애니메이션 시작, 끝 효과

```

- Text 트위닝 함수:
```C#
Text txt = GetComponent<Text>();
text.DOText("DOTween Example", 2, true, ScrambleMode.All).SetDelay(2); // 글자가 나올때 이리저리 섞여서 나오는 효과
```

**컴포넌트마다 할 수 있는게 다 다르다!**

>[!question] 그럼 그걸 다 외워야하나요?

>[!tip] 여기 다 있다. [DOTween 공식홈페이지](https://dotween.demigiant.com/documentation.php)

---
## 유료 버전
#### 무려 코딩 외에도 컴포넌트를 넣을 수 있다.

![[Pasted image 20240107221453.png]]

파란 None 부분을 클릭하여 사용할 애니메이션을 선택할 수 있다.
Play / Stop 버튼을 클릭하여 굳이 게임을 실행하지 않고도 애니메이션을 미리보기 할 수 있다.
- Move 함수 사용 예시 :
![[Pasted image 20240107221801 1.png]]

---
## 참고자료

[트위닝 최강 에셋, 두트윈 DOTween](https://www.youtube.com/watch?v=SZF1oZ-tqMs&t=604s)

---
+써본 결과, 인스펙터 창에서 하는 것이 편할 때도 있고, 코드로 짜서 처리하는 것이 편할 때도 있음.
(예를 들면, 클릭시 일어나는 트위닝은 인스펙터에서 처리할 수 없기에 코드로 짜서 처리해야 함.)