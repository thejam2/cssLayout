# cssLayout
cssLayout 연습

flex

display:flex	//바로위 부모한테 적용해야함 (inline-block같은 효과)

flex의 세계에는 두 가지가 있다.
1. row(행): 가로를 의미.  //디폴트
2. column(열): 세로를 의미.

flex diretion이 row일때
main axis -> 가로
cross axis -> 세로

main axis 조절시 justify-content
cross axis 조절시 align-items

align-self

align-self CSS 속성은 하나의 그리드 또는 하나의 플렉스 아이템의 align-items 값을 재정의합니다.
(하나의 엘리먼트에 align-items값을 개별적으로 주는 것이다.)

order

order CSS 속성은 플렉스 또는 그리드 컨테이너 안에서 현재 요소의 배치 순서를 지정합니다. 컨테이너 아이템의 정렬 순서는 오름차순 order 값이고, 같은 값일 경우 소스 코드의 순서대로 정렬됩니다. Flex 항목의 기본 order 값은 0이므로 0보다 큰 정수 값을 가진 항목은 지정되지 않은 항목 뒤에 표시됩니다.
(order는 숫자 값이 적을 수록 앞에 배치됨)
참고: order 속성은 논리적인 순서나 탭 순서와는 전혀 상관 없이 화면에 보이는 순서에만 영향을 줍니다. 따라서 비시각적 매체에 적용해선 안됩니다.
