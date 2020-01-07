# IntelliJ 단축키 (Mac OS X)

*Assembled by GimunLee (2020-01-07)*

<br/>

## 기호 설명

- #### `⌘` : command

- #### `⌃` : control

- #### `⇧` : shift

- #### `⌥` : option(alt)

- #### `⎋` : esc

- #### `⏎` : return(enter)

- #### `⇥` : tab

<br/>

## File

- `⌘(command)`  +  ` O` : 클래스 찾기 // 대소문자 구분

- `⌘(command)`  +  `⇧(shift)`  +  `O` : 파일 찾기 // 유사 단축키로 `⇧(shift)` +  `⇧(shift)` 도 많이 사용
- `⌘(command)` + `E` : 최근 사용 파일 찾기
- `⌃(control)` +  `⇥(tab)` : 최근 파일로 이동 // 위 `⌘(command)` + `E` 와 유사하나 UX가 약간 다름

<br/>

## Layout

- `⌘(command)` + `1` : Project view
- `⌘(command)` + `3` : Find view
- `⌘(command)` + `4` : Run view
- `⌘(command)` + `6` : TO DO
- `⌘(command)` + `8` : Hierarchy // `⌃(control)` + `⌥(option)` + `H` 로 메소드 호출을 찾으면 노출됨
- `⌘(command)` + `9` : Version Control // git, task 관리
- `⇧(shift)` + `⎋(esc)` : 활성화된(현재 선택된) Layout 닫기

<br/>

## Refector - 강추

- `⌘(command)` + `⌥(option)` + `M` : 메서드 분리
- `⌘(command)` + `⌥(option)` + `C` : 상수 분리 생성 (`public static final ...`)
- `⌘(command)` + `⌥(option)` + `F` : 필드(객체변수) 분리
- `⌘(command)` + `⌥(option)` + `V` : 지역변수 분리

<br/>

## Editor

- `⌥(option)` + `⏎(enter)` : Quick fix - 오류 해결 솔루션 제시 // **강추**
- `⌘(command)` + `⇧(shift)` + `↑` : 선택된 코드 영역 위 블럭 단위로 이동
- `⌘(command)` + `⇧(shift)` + `↓` : 선택된 코드 영역 아래로 블럭 단위로 이동
- `⌘(command)` +  `Del` : 한 줄 삭제
- `⌘(command)` + `⇧(shift)` + `]` : 에디터 탭 기준 오른쪽으로 이동
- `⌘(command)` + `⇧(shift)` + `[` : 에디터 탭 기준 왼쪽으로 이동
- `⌥(option)` + `↑` : 커서 기준으로 단위 영역(단어, 영역, 문장, 메서드 등) 선택  // **강추**
- `⌘(command)` + `F12` : 현재 클래스 필드, 메서드 등 목록 노출 // lombok 사용할 시 편함
- `⌘(command)` + `N` : 각종 코드 생성 (getter, setter, override, DI 등)
- `⌃(control)` + `O` : 상위클래스 override
- `⌃(control)` + `⌥(option)` + `O` : Auto import
- `⌥(option)` + `⇥(tab)` : 스플릿(화면분할) 상태에서 화면 간 이동
- `⌥(option)` +  `F1` then `1` or `⏎(enter)` : 현재파일 Project View 에서 활성화

<br/>

## 실행

- `⌘(command)` + `F9` : 컴파일
- `⌘(command)` + `R` : Run View에서 현재 포커싱 실행 // 실행 중이면 재실행
- `⌘(command)` + `F2` : Run View에서 현재 활성화된 실행을 Kill
- `⌃(control)` + `R` : 최근 실행한 것을 다시 실행
- `⌃(control)` + `⌥(option)` + `R` : 현재 커서나 포커싱 된 파일에 실행가능한 것을 노출 후 선택 실행 가능
  - 보통 단위테스트 시 해당 커서가 메서드 안에 있는 상태에서 위 단축키를 누르고 `2` 를 누르면 바로 메소드 테스트 실행
- `⌃(control)` + `D` : 최근 실행한 것을 다시 실행 // 디버깅 모드
- `⌃(control)` + `⌥(option)` + `D` : 현재 커서나 포커싱 된 파일에 실행가능한 것을 노출 후 선택 실행 가능 // 디버깅 모드

<br/>

## 생성

- `⌘(command)` + `⇧(shift)` + `T` : 테스트케이스생성
  - 이후 `⌘(command)` + `N` 을 이용하면 테스트 메서드 생성이 편리함

<br/>

## 이동

- `⌘(command)` + `B` : 클라이언트 코드에서 해당 메소드 선언으로 이동
- `⌘(command)` + `⌥(option)` + `B` : 클라이언트 코드에서 해당 메소드 구현으로 이동 // **강추**
- `⌘(command)` + `U` : 구상클래스에서 해당 메소드 선언으로 이동
- `⌘(command)` + `⌥(option)` + `←` , `⌘(command)` + `⌥(option)` + `→` : 이전, 다음 작업영역으로 이동

<br/>

## 작업(형상)관리

- `⌘(command)` + `K` : Commit
  - 커밋 확인 후 `⌃(control)` + `⏎(enter)` 를 치면 됨
  - 만약 review 여부를 물으면 Commit 버튼을 `⇥(tab)` 으로 포커싱 후 `Space` 를 입력
- `⌥(option)` + `⇧(shift)` + `N` : Task 추가 - `⌘(command)` + `9` 와 연계하면 작업관리 시 편함
- `⌥(option)` + `⇧(shift)` + `C` : Recent Changes

<br/>

## Multiline

- `⌘(command)` + `⌃(control)` + `G` : 커서가 위치한 단어 기준 multiline 제어
- `⌘(command)` + `⇧(shift)` + `8` + `⇧(shift)` + `↑` , `⇧(shift)` + `↓` : multiline 모드 활성화 후 라인 선택
- `⌥(option)` + `⇧(shift)`  + `MouseLeftClick` : 마우스로 클릭한 위치 기준으로 multiline 제어

<br/>

## 검색

- `⌘(command)` + `⇧(shift)` + `F` : 문자열 전체 검색

<br/>

## 바로가기

- `⌘(command)` + `,` : 환경설정
- `⌘(command)` + `;` : 프로젝트 환경설정

<br/>

## Syntax

- `iter` : for-each 구문 생성
- `fori` : for 구문 생성
- `psfs` : `public static final String`
- `psfi` : `public static final int`
- `psvm` : `public static void main(String[] args)`
- `thr` : `throw new`

<br/>

## Reference & Additional Resources

- http://redutan.github.io/2016/03/23/intellij-favorite-keymap-osx