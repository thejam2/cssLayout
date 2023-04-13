# cssLayout
cssLayout 연습

## flex

display:flex	//바로위 부모한테 적용해야함 (inline-block같은 효과)

flex의 세계에는 두 가지가 있다.
1. row(행): 가로를 의미.  //디폴트
2. column(열): 세로를 의미.

flex diretion이 row일때
main axis -> 가로
cross axis -> 세로

main axis 조절시 justify-content
cross axis 조절시 align-items

### align-self
align-self CSS 속성은 하나의 그리드 또는 하나의 플렉스 아이템의 align-items 값을 재정의합니다.
(하나의 엘리먼트에 align-items값을 개별적으로 주는 것이다.)

### order
order CSS 속성은 플렉스 또는 그리드 컨테이너 안에서 현재 요소의 배치 순서를 지정합니다. 컨테이너 아이템의 정렬 순서는 오름차순 order 값이고, 같은 값일 경우 소스 코드의 순서대로 정렬됩니다. Flex 항목의 기본 order 값은 0이므로 0보다 큰 정수 값을 가진 항목은 지정되지 않은 항목 뒤에 표시됩니다.
(order는 숫자 값이 적을 수록 앞에 배치됨)
참고: order 속성은 논리적인 순서나 탭 순서와는 전혀 상관 없이 화면에 보이는 순서에만 영향을 줍니다. 따라서 비시각적 매체에 적용해선 안됩니다.


### flex-wrap
flexbox는 width보다도, '같은 줄'에 있도록 하는 것을 우선시함

`flex-wrap: wrap;` (child의 사이즈를 유지하라고 하는 것)

nowrap; (child를 모두 같은 줄에 정렬함, 이때 width가 줄어들 수 있음, 디폴트)

### reverse
`flex-direction: row-reverse;` (오른쪽에서부터 1이 시작)

`flex-wrap: wrap-reverse;` (한 줄이 되지 않아도 아래에서 위로 정렬되게)

### align-content
justify-content와 비슷하지만 'line'에 관한 것 (각 block이 여러 행에 걸쳐 나올 때, 행간 공백을 얼마나 둘 건지?)

ex) `align-content: flex-start; - align-content: space-around;`

### flex-shrink
flexbox가 작아질 때, element의 행동의 정의함(디폴트값 1)

ex) `flex-wrap: nowrap`일때, 화면이 작아지면 width가 설정되어있어도 줄어듬.

`flex-shrink: 1; flex-shrink: n(정수);` --> 여러 개 element 중 특정 element만 덜 줄어들거나, 더 줄어들게 할 수 있음


### flex-grow
shrink와 반대, 화면이 늘어남에 따라 box 크기가 얼마나 늘어날지 설정(디폴트값 0)

flex-grow: 1; flex-grow: 0; 남아있는 공간을 가져옴 (space를 없애고)

남아있는 공간, 여백이 있을 때만 grow 가능

화면이 커질 때, element도 함께 커지길 원할 때 사용

flex-grow property가 0인 상태거나, 따로 정의되지 않았다면, 화면이 커져도 각 element 크기가 커지지 않음 (여백만 늘어나게 됨)


### flex-basis
shrink, grow 되기전에 element에게 초기 size를 줌

but 자주 사용 X basis 정의 안할시 width와 같은 값이니까.


### flex 연습 사이트 : https://flexboxfroggy.com/#ko

-----------------------------------------------------------------------------------

## grid

### grid-template-rows
그리드 행의 크기 조절

### grid-template-columns
그리드 열의 크기 조절

### gap
gap은 행과 열 사이의 간격을 설정합니다.

row-gap 및 column-gap의 단축어입니다.
```
gap: 10%;
gap: 10px 20px;
gap: calc(20px + 10%);
```

grid-template-columns와 grid-template-rows에서 `repeat(개수, 크기)`으로 더 쉽게 할 수 있다.

auto를 사용하면 최대한 크게 만들어준다.


### grid-template-areas
grid-area에 있는 이름과 grid-template-areas에 있는 이름이 같아야 한다.

class 이름은 상관없다.
```
.grid {
    display: grid;
    grid-template-columns: auto 200px;
    grid-template-rows: 100px repeat(2, 200px) 100px;
    grid-template-areas:
      "header header header header"
      "content content content nav"
      "content content content nav"
      "footer footer footer footer";
  }
  
  .header {
    background-color: #2ecc71;
    grid-area: header;
  }
```

### grid-column-start, grid-row-start
grid-column-start는 그리드 배치에 line, span을 통해 그리드 열 내에서 그리드 아이템의 시작 위치를 지정합니다.

이 시작 위치는 그리드 영역의 블록 시작 가장자리를 정의합니다.

```
grid-column-start: auto;
grid-column-start: 2;
grid-column-start: -1;  (마지막라인= -1)
grid-column-start: span 2; (줄이 아닌 블럭의 영역을 지정)
```

### grid-column-end, grid-row-end

그리드 항목의 끝 위치를 지정함으로써 그리드 영역의 블록 끝 가장자리를 지정합니다.

```
grid-column: (start) / (end);
grid-row: (start) / (end);
```

-1, -2, -3, ··· -> 끝에서부터 line 세기

(start) / span (cell 수) -> 시작점과 끝점을 적는걸 대신한다.

### fr
fr-fraction(부분)
fraction은 grid에서 사용 가능한 공간을 뜻한다.
fr값 비율로 공간을 나눈다.

### grid-template
```
"(이름)" (row크기)
"(이름)" (row크기)
"(이름)" (row크기)/ (각 column의 크기);
```
grid-template에서는 reapeat 안됨


### place items
```
justify-items : 수평
align-items : 수직
place-items: (수직) (수평);
stretch : grid를 늘려서 grid를 채우게 한다.
start : item을 cell 시작에 배치한다.
center : item을 cell 중앙에 배치한다.
end : item을 cell 끝에 배치한다.
```

### place content
```
justify-content : 수평; /*(그리드가 놓이는 위치를 뜻하며 기본은 start)*/
align-content : 수직;
place-content : 수직 수평;
start, end, space-evenly, space-around, space-between 사용
```

컨테이너의 height가 그리드를 담을 만큼 충분해야한다.(높이 지정)

place-items는 셀안에서 항목이 이동하는 것이며, place-content는 그리드가 이동하는 것


### place self
```
align-self : 수직
justify-self : 수평
place-self: 수직 수평;
//child에만 적용돠는 property이다.
```

`grid-auto-rows: 크기;`
만들어놓은 row보다 더 많은 content가 있으면, 자동으로 row를 만들어라.

```
grid-auto-flow: 방향; [기본값: row]
flex-direction과 비슷
row가 끝날 때 새로운 row를 만들지, 새로운 column을 만들지 결정한다.
```

```
grid-auto-columns: 크기;
grid-auto-flow: column;일때 작동.
```


### minmax
`grid-template-columns: repeat(5, minmax(100px, 1fr));` =>최소 100px, 최대 1FR


### auto-fill, auto-fit
```
Grid-template-columns: repeat(auto-fill, minmax(100px, 1fr)); //창 너비가 늘어나면 빈 column들로 row를 채움
Grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)); // 창 너비가 늘어나면 element를 늘려서 row에 맞게 해줌
```


### max-content
content의 크기만큼 cell의 크기를 늘린다.

### min-content
content의 크기를 최대한 줄여 cell의 크기를 줄인다.

