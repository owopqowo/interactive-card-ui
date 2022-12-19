# 학습 내용 정리
## hsl 사용이유
### hsl
색상(Hue), 채도(Saturation), 명도(Lightness) 값으로 색상 지정
### rgb, 16진법의 문제점
1. 직관적이지 않음
2. 유지보수의 어려움 (색상별로 많은 음영이 필요 시)
### 사용예시
```
/**common-colors**/ 
:root{
  /* base color 1 */
  --base-color1: 60;
  --color1-light:  hsla(var(--base-color1), 50%, 75%, 100%);
  --color1-normal: hsla(var(--base-color1), 50%, 50%, 100%);
  --color1-darker: hsla(var(--base-color1), 50%, 35%, 100%);
  
  /* base color 2 */
  --base-color2: 120;
  --color2-light:  hsla(var(--base-color2), 50%, 75%, 100%);
  --color2-normal: hsla(var(--base-color2), 50%, 50%, 100%);
  --color2-darker: hsla(var(--base-color2), 50%, 35%, 100%);
  
  /*base color 3 */
  --base-color3: 200; 
  --color3-light:  hsla(var(--base-color3), 50%, 75%, 100%);
  --color3-normal: hsla(var(--base-color3), 50%, 50%, 100%);
  --color3-darker: hsla(var(--base-color3), 50%, 35%, 100%);
  
  /** commonly used saturation/lightness/opacity levels **/ 
  --saturation-level1: 20%;
  --saturation-level2: 50%; /* mid range - normal */
  --saturation-level3: 80%;
  
  --lightness-level1: 75%;
  --lightness-level2: 50%; /* mid range - normal */
  --lightness-level3: 35%;
  
  --opacity-level1: 100%; /* no opacity - normal */
  --opacity-level2: 80%;
  --opacity-level3: 60%;
  
  --color1-light: hsla( var(--base-color1), var(--saturation-level2), var(--lightness-level1), var(--opacity-level1) );
}
```
## CSS min()
2개 이상의 대소비교가 가능한 값이 주어졌을 때, 그 중에서 작은 값을 반환
### 사용예시
max-width 대체하여 사용가능
```
.content {
  width: 70%;
  max-width: 1000px;
}

.content {
  width: min(70%, 1000px);
}
```
## CSS aspect-ratio
요소의 크기를 비율대로 줄이거나 늘리는 데 사용
### 과거 종횡비 조절법
#### 단순지정
width와 height를 지정
응형을 구현하는데 어려움
```
.box {
  width: 200px;
  height: 100px;
}
```
#### padding을 사용
padding-top 또는 padding-bottom을 이용하는 방법
```
.box {
  width: 200px;
  padding-top: 50%;
}
.box {
  width: 200px;
  padding-top: calc(100% / 16 * 9);
}
```
### 최신 종횡비 조절법
```
.box {
  width: 200px;
  aspect-ratio: 16 / 9;
}
```
####  종횡비 auto 지정
요소가 고유한 종횡비를 가지는 경우 auto로 해당 종횡비를 따른다.  
요소가 고유한 종횡비를 가지지 않는 경우 지정한 비율 속성값에 따른다.
```
.box {
  width: 200px;
  aspect-ratio: auto 1 / 1;
}
```
#### 이미지 종횡비 강제 지정
```
.img {
  width: 200px;
  object-fit: cover;
  aspect-ratio: 16 / 9;
}
```
#### 예외 상황
width, height 값이 지정될 경우 종횡비 적용 ❌  
내용이 요소를 넘는 경우 요소는 확장되지만 종횡비 적용 ❌
