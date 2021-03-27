# 확장 문법
- 비쥬얼스튜디오코드에서는 적용이 안되는 것도 있음 깃허브에 가면 적용됨.

## 표 (확장)

### 생성
> 표를 추가하고싶으면 3개 이상의 하이픈(`-`)으로 각 열의 헤더를 구분해준뒤 `|` 로 열을 분리할수 있다. 셀의 가로 길이는 자동조정된다.
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
### 정렬
> 3개 이상의 하이픈(`-`)ㅇ,로 각 열의 헤더를 구분할때 ":"의 위치로 정렬을 할 수 있다. 세미콜론이 왼쪽에 붙으면 왼쪽 정렬 오른쪽에 붙으면 오른쪽 정렬 양쪽에 붙으면 가운데 정렬이다.
```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
### 추가적인 것들
> 첫 행에 파이프를 양 끝에 붙였다면 다음 행부터는 안붙여도 된다. 단 비어있는 셀일 경우에는 파이프로 구분을 해줘야 한다.
```
| abc | defghi |
:-: | -----------:
bar | baz
|    |aaa|
```
| abc | defghi |
:-: | -----------:
bar | baz
|    |aaa|
> 헤더를 구분해주는 하이픈은 반드시 열의 개수만큼 있어야 한다. 없으면 표로 인식되지 않는다.
```
| abc | def |
| --- |
| bar |
```
| abc | def |
| --- |
| bar |
> 헤더를 구분해 준다면 밑의 항목들은 비어있어도 되고 넘치면 자동으로 잘린다.
```
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |
```
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |

## 리스트 버튼
> "-"와 스페이스바 한칸 하고 "[ ]"를 붙인뒤 스페이스바 한칸 하고 버튼명을 적으면 된다.
```
- [ ] foo
- [x] bar
```
- [ ] foo
- [x] bar
> 중첩 리스트 또한 가능 하다.
```
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim
```
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim

## 취소선
> 취소선을 넣고싶은 문장의 앞뒤에 "~"를 2번 써주면 된다.
```
~~Hi~~ Hello, world!
```
~~Hi~~ Hello, world!

> 단 구문이 분리 되있으면 적용되지 않는다.
```
This ~~has a

new paragraph~~.
```
This ~~has a

new paragraph~~.

## 자동링크
>자동링크는 `<`, `>` 없이 만들어진다. 모든 자동링크는 줄의 시작, 공백 뒤에 또는 구분문자(`* , _ , ~ , (`) 뒤에 올 수 있다.

> 추가로 http는 자동으로 삽입된다.
```
www.commonmark.org
```
www.commonmark.org

> url 앞 뒤는 공백을 넣어줌으로써 구분해준다.
```
Visit www.commonmark.org/help for more information.
```
Visit www.commonmark.org/help for more information.

> 링크 안에 구두점(`? ! . , : * _ ~)이 와도 링크로 인식이 됩니다.
```
Visit www.commonma?rk.c!o:*_m.a~.b.
```

Visit www.commonma?rk.c!o:*_m.a~.b.

> 닫는괄호가 여는괄호보다 많을때는 별 신경 안써도 된다. 자동으로 남는 닫는 괄호는 문자 처리 된다.
```
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)
```
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)

> 링크가 `)` 로 끝나면 뒤에 공백이 없으면 계속 링크로 인식을 한다.
```
www.google.com/search?q=(business))+ok+OK-ok
```
www.google.com/search?q=(business))+ok+OK-ok

> 자동링크가 `&HTML엔티티이름;`으로 끝나면 제외된다.
```
www.google.com/search?q=commonmark&amp;
```
www.google.com/search?q=commonmark&amp;

> "<" 는 즉시 자동링크를 끝낸다.
```
www.commonmark.org/he<lp
```
www.commonmark.org/he<lp

## 이메일 자동링크
> 이메일도 자동링크가 된다. 앞에 mailto:가 자동으로 붙는다.

> 규칙 
1. 1개 또는 그 이상의 문자나 숫자 또는 `. - _ +` 가 온다.
2. `@` 가 1개 있어야한다.
3. 1개 또는 그 이상의 문자나 숫자 또는 `- _`는 `.` 으로 구분된다. 적어도 1개의 구분이 되야한다.

```
foo@bar.baz
```
foo@bar.baz

> `+` 는 `@` 앞에 오면 안되고 `@` 뒤에 와야 한다.
```
hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.
```

hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.

> 마지막 문자는 `- _` 로 끝나면 안된다.
```
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_
```
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_
# 허용되지 않은 HTML 태그

> 밑의 태그들은 필터되서 결과에 출력되지 않는다.

* `<title>`
* `<textarea>`
* `<style>`
* `<xmp>`
* `<iframe>`
* `<noembed>`
* `<noframes>`
* `<script>`
* `<plaintext>`