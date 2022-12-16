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
