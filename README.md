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
## CSS inset
요소의 위치를 결정하는 top, right, bottom, left의 축약 스타일 속성
### 사용예시
top, right, bottom, left 값을 한줄로 작성 가능
```
.box {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

.box {
  position: absolute;
  inset: 0;
}
```
## Sass @for
### 사용예시
@for 문을 작성할 때 변수는 보간법(#{})으로 처리
```
/* SCSS */
@for $i from 1 to 3{
  .icon_#{$i}{
    background-position:0 ($i * -10px);
  }
}

/* CSS */
.icon_1{background-position:0 -10px;}
.icon_2{background-position:0 -20px;}
```
### from ~ to와 from ~ through 차이점
#### from ~ to
to 뒤에 나오는 숫자 미만의 반복되는 값을 사용 (해당 숫자 비포함)
```
/* SCSS */
@for $i from 0 to 5{
  .animal_#{$i}{
    background-position:0 ($i * -10px);
  }
}

/* CSS */
.animal_0{background-position:0 0;}
.animal_1{background-position:0 -10px;}
.animal_2{background-position:0 -20px;}
.animal_3{background-position:0 -30px;}
.animal_4{background-position:0 -40px;}
```
#### from ~ through
through 뒤에 나오는 숫자 이하로 반복되는 값을 사용 (해당 숫자 포함)
```
/* SCSS */
@for $i from 0 through 5{
  .animal_#{$i}{
    background-position:0 ($i * -10px);
  }
}

/* CSS */
.animal_0{background-position:0 0;}
.animal_1{background-position:0 -10px;}
.animal_2{background-position:0 -20px;}
.animal_3{background-position:0 -30px;}
.animal_4{background-position:0 -40px;}
.animal_5{background-position:0 -50px;}
```
