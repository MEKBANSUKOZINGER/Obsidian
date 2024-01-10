## touchCount
Input 클래스에 \[touchCount] 라는 속성이 있는데, 모바일 장치 화면에 접촉되어있는 손가락의 개수를 의미한다.

```C#
Input.touchCount; // 화면에 접촉한 손가락의 개수
```

---
## GetTouch
Input 클래스의 GetTouch 메소드는 모바일 장치 화면에 접촉한 손가락의 순서에 해당하는 Touch 구조체를 반환한다.
**+응용 :** GetTouch로 얻은 구조체에다 .position을 이용해 터치한 위치를 알아낼 수 있다.
**++응용 :** Touch 구조체의 **deltaPosition**은 가장 마지막 프레임에서 발생했던 터치의 위치와 현재 프레임에서 발생한 터치 위치 차이를 알려준다. 이 것을 이용해 터치의 이동방향을 추적할 수 있다.

```C#
Input.GetTouch(0).position; // 맨 처음 터치한 손가락의 위치
Input.GetTouch(0).deltaPosition; // 맨 처음 터치한 손가락의 위치 변화
```

---
## tapCount
Touch 구조체의 tapCount는 특정 위치에 접촉되어있는 손가락에서 연속적으로 일어난 탭의 수를 알려준다.

```C#
Touch.tapCount;
```

---
## TouchPhase
TouchPhase는 가장 최근의 프레임에서 손가락이 취한 동작을 나타낸다.

| TouchPhase | 역할 |
| ---- | :--: |
| Began | 손가락이 화면을 터치하는 그 순간 |
| Moved | 손가락이 화면 위에서 터치한 상태로 이동하고 있는 상태 |
| Stationary | 손가락이 화면을 터치했지만, 마지막 프레임에서 변화가 없는 상태 |
| Ended | 손가락이 화면 위를 벗어나 떨어지게 되는 그 순간, 터치가 끝난 상태 |
| Canceled | 5개 이상의 터치 입력이 동시에 발생해서 시스템이 터치의 추적을 취소한 상태 |

- TouchPhase를 확인하는 간단한 코드
```C#
void Update() {
	if (Input.touchCount > 0) { // 터치가 발생했을 경우 (접촉한 손가락이 0개 초과)
		Touch touch = Input.GetTouch(0); // 맨 처음 터치한 손가락의 구조체 받아오기
		if (touch.phase == TouchPhase.Began) { // 손가락이 화면을 터치한 그 순간
			Debug.Log("Began : " + touch.poisiton);
		}
		if (touch.phase == TouchPhase.Moved) { // 손가락이 터치하고 움직이는 상태
			Debug.Log("Moved : " + touch.position);
		}
		if (touch.phase == TouchPhase.Ended) { // 손가락이 떨어진 순간
			Debug.Log("Ended : " + touch.position);
		}
	}
}
```

---
## 참고자료

[유니티 터치 (Touch) 입력 기초](https://m.blog.naver.com/pxkey/221312986925)

---
