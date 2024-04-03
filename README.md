## Code Flow Chart

![printcodeflow](https://github.com/AriSongYe/ft_printf/assets/82326075/9ac26b65-a1bd-47f0-93ca-169e64e25698)

## 필요 개념

[서식 지정자 & flag](https://www.notion.so/format-specifier-flags-44c3520ed7254d0f90daa897ca22a326?pvs=4), [가변 인자](https://www.notion.so/Variadic-argument-5b7f135b0cac48a2b4afcede580f109a?pvs=4), parsing

중요한건 parsing이다 읽고 넘겨주고 다시 읽는 구조를 잘 짜는게 중요하다.

<aside>
💡 여기서 parsing이란, 구문 분석 혹은 구성 분석이다.

즉, 원하는 부분을 tokenize해서 사용자 임의로 분리하는 작업을 통칭해서 parsing이라 하는 것 같다.

</aside>

Mandatory 부분은 어찌되었든 ‘%’ 문자 다음만 읽으면 끝이었지만

BONUS 파트는 서식지정자를 만날 때까지 플래그를 만날 수도 만나지 않을 수도 있다.

그 인덱스와 출력하는 문자의 개수를 그 때 그 때 저장하고 파악하는 것이 중요할 것으로 판단된다.

서식지정자는 앞에서 mandatory를 구현하며 알아보았기에

먼저 flag를 정리하자!

| ‘-’ | 왼쪽 정렬, defalut는 오른쪽 정렬 |  |
| --- | --- | --- |
| ‘+’ | 양수일지라도 ‘+’ sign을 앞에 추가해서 출력, defalut : 음수만 ‘-’ sign 출력 |  |
| ‘ ‘ | 양수일 때는 부호를 생략하고 공백으로 표시한다. 단, 음수일 때는 -를 표시한다. |  |
| ‘#’ | 각 진법과 형식에 맞게 0, 0x, 0X를 추가한다.
type 필드의 c, s, d, i, u옵션과 사용되면 #를 무시한다. |  |
| ‘0’ | width 필드에 주어진 옵션자리에 맞춰 빈 자리에 0을 추가하고, - (minus)와 사용될 경우 좌측 정렬을 하기 때문에 무시하게 된다.
type 필드의 수를 표기하는 d, i, o, u, x, X를 사용할 때 .preicison 필드도 함께 이용되면, 주어진 옵션만큼 빈 자리를 0으로 채운다. |  |

실제 printf에서 저 옵션들을 사용해보는게 제일 이해하기에 편하다!
