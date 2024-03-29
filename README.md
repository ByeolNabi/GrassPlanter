# Grass-Planter
친구들과 1일 1커밋을 도전하고 있는데 매번 들어가서 '커밋했나...?' 하는 것이 힘들었습니다. ~~(사실 확인해 본 적 없습니다.)~~<br>
따라서 한 곳에 모아보면 편할 것 같아서 시작했습니다.

## 도전과제

[1. 깃허브 잔디 데이터 가져오기](#1.-깃허브-잔디-데이터-가져오기)<br>
[2. 깃허브 잔디 데이터 출력하기](#2.-깃허브-잔디-데이터-출력하기)<br>
[3. 도전 참여자들의 잔디 출력하기](#3.-도전-참여자들의-잔디-출력하기)<br>

### 수행과정
#### 1. 깃허브 잔디 데이터 가져오기
**수행방법** :
F12를 눌러서 dev모드를 이용해 잔디를 가져오는 링크를 알아낸다.<br>
네트워크 탭에 들어간 상태로 잔디밭의 년도를 바꿔보면 링크가 튀어나온다.
https://github.com/users/ByeolNabi/contributions?from=2023-12-01&to=2023-12-31

#### 2. 깃허브 잔디 데이터 출력하기
**전략** :
뭔가 fetch를 사용해서 결과값 받아오면 될 것 같다. 다만, 잔디에 해당하는 태그들에게 어떤 css를 적용할지를 고민해봐야 할 것 같다. <br>
**수행** :
CORS가 나를 막아선다👍, 브라우져에서 웹으로 직접 접근이 되길래 fetch를 사용했는데 바로 CORS.<br>
그냥 그림을 만들어주는 api를 사용하기로 했다.<br>
```<img src="https://ghchart.rshah.org/Byeolnabi" alt="Byeolnabi's chart">```를 사용하면 된다.<br>
🤔이 api는 어떻게 만든 것일까? CORS를 어떻게 뚫고간거지<br>
🙄생각해보니 웹사이트를 만들 필요도 없었다. 이미지이기 때문에 그냥 마크다운에 넣어놔도 볼 수가 있구나... (~~모르는 척 넘어가기로 하자.~~)<br>
![Byeol'sPic](https://ghchart.rshah.org/Byeolnabi)

#### 3. 도전 참여자들의 잔디 출력하기
**전략** :
도전 참여자들은 파일로 관리를 하는 편이 좋을 것 같다. config같은 곳에 저장해두고 js를 이용해서 태그를 반복시키자.<br>
**수행** :
config에 저장되어 있는 멤버의 수만큼 반복되게 만들었다. 저번에 들었던 강의의 코드를 참고하였다<br>
createElement("div")를 이용하여서 div안에 문자 리터럴을 innerHTML을 이용해서 덮어씌운 다음 appendChild(```object```)를 이용했다. appendChild는 문자 리터럴을 받을 수 없기 때문에 div를 만들어 리터럴 감싸기를 했다.<br>
❗️script의 위치는 중요하다. 아직 로드되지 않은 html을 불러오는 행동을 하지 말자.

**개선사항**<br>
📌config.json을 좀 더 아름답게 로드하는 방법을 알아보자. 소스파일이 보이게 되어서 개인정보 다 털리게 생겼다.

#### 4. 잔디 데이터를 어떻게 받아올 수 있을지 조사하기
**전략** :
오픈소스 코드를 보면 될 것 같긴 하다.
어떤 식으로 데이터를 가져왔는지 보자.

### 팁
---
웹 페이지는 위에서부터 아래로 로드된다.js에서 태그의 내용을 수정하는 명령이 있다면, Tag보다 js가 아래에 있어야 작동할 것이다.