## 객체
: 객체 내부 값들은 '속성'이라고 불리고, 속성 중 함수 자료형은 '메소드'라고 칭함
1. 사용법 - 키: 값
   1) 예시
      ```javascript
      const me = {
        name: 'Jayo',
        age: 22,
        nationality: 'Korea' 
      }
      ```
      => 이런 식으로 중괄호를 사용하여 객체를 생성하고, 쉼표(,)로 연결함
   2) 객체 요소에 접근하는 법
      * 방법(1): \[대괄호\]와 '따옴표' 사용하기
        me\['name'\]
      * 방법(2): 온점(.) 사용하기 => 더 많이 사용됨
        me.name
      ※ 대부분은 방법(2)를 사용하지만 식별자로 사용할 수 없는 단어(ex.문자열)을 키값으로 사용했을 경우에는
         무조건 대괄호를 사용해야 요소에 접근할 수 있다.
2. 메소드 내부에서 this 키워드 사용하기
   : 자기 자신이 가진 속성을 표시할 때 'this' 키워드 사용
   1) 예시
      ```javascript
      const pet = {
        name: '구름',
        eat: function(food){
            alert(this.name+'은/는'+food+'을/를 먹습니다.'
        }
      }
      pet.eat('밥)
      /*
      <결과>
      구름은/는 밥을/를 먹습니다.
      */
      ```
3. 동적 속성 추가
   : 객체 생성 후에 속성을 추가하는 것
   1) 사용법
      * 객체.속성 = 값
      * 객체\['속성'\] = 값
      ```javascript
      const student = {}
      student.name = '철수'
      //또는 student['name'] = '철수'
      student.hobby = '악기'
      /*
      <결과>
      {
        "name": "철수"
        "hobby": "악기"
      }
      */
      ```
4. 동적 속성 제거
   : delete 키워드 사용
   1) 사용법
      * delete 객체.속성
      * delete 객체\['속성'\]
      ```javascript
      const student = {}
      student.name = '철수'
      student.hobby = '악기'
      delete student.hobby
      //또는 delete student['hobby']
      /*
      <결과>
      {
        "name": "철수"
      }
      */
      ```

## 객체의 속성과 메소드
1. 기본 자료형 -> 객체 자료형
   1) 기본 자료형을 객체로 선언하는 법
      const 객체 = new 객체 자료형 이름()
      * 예시
        - new Number(10)
        - new String('안녕하세요')
        - new Boolean(true)
      => 이런 식으로 변환하면 속성과 메소드 모두 활용 가능
   2) 기본 자료형의 일시적 승급
      : JS는 기본 자료형의 속성과 메소드를 호출할 때, 즉 기본 자료형 뒤에 온점을 찍고 무언가 하려고 하면
        일시적으로 기본 자료형을 객체로 승급시킴.
      => 속성 추가 가능. 그러나 일시적 승급이기 때문에 추가됐던 속성은 바로 사라짐
      * 예시
        ```javascript
        const h = '안녕하세요' // undefined
        h.sample = 10 // 10 -> 속성 추가 가능
        h.sample // undefined -> 그러나 재호출 시 이미 사라짐
        ```
   3) prototype으로 메소드 추가하기
      : prototype 객체에 속성과 메소드 추가 -> 모든 객체&기본 자료형에서 해당 속성과 메소드 사용 가능
      * 사용법: 자료형 이름.prototype.메소드 이름 = function () {...}
      * 예시1
        ```javascript
        // 숫자 자료형에 n제곱하는 메소드 추가하기
        Number.prototype.power = function (n=2) {
           return this.valueOf() ** n
        }
        const a = 12
        console.log('a.power():', a.power()) // 제곱
        console.log('a.power(3):', a.power(3)) // 세 제곱
        console.log('a.power(4):', a.power(4)) // 네 제곱
        ```
      * 예시2 - 문자열과 배열이 indexOf() 메소드
        ```
        // 문자열의 indexOf() 메소드
        const j = '안녕하세요'
        j.indexOf('안녕') > 0 출력
        => 인덱스를 출력. 문자열 내에 없는 문자열이라면 -1 출력
        // 배열의 indexOf() 메소드
        const k = [1, 2, 3]
        k.indexOf(2) > 2의 인덱스인 1을 출력한다
        => 역시나 배열 내에 없는 요소라면 -1 출력
        ```

4. Number 객체
   1) toFixed(): 소수점 이하 N번째 자리까지만 출력하기 - 반올림 법칙 적용
      * 예시
        ```
        const l = 123.15392
        console.log(l.toFixed(2)) > 123.15
        // 두 번째 자리의 5 > 세 번째 자리의 3 => 반올림 법칙에 따라 그대로 놔두기
        console.log(l.toFixed(3)) > 123.154
        // 세 번재 자리의 3 < 네 번째 자리의 9 => 반올림 법칙에 따라 3을 4로 올림 -> ~.154
        console.log(l.toFixed(4)) > 123.1539
        // 네 번째 자리의 9 > 다섯번째 자리의 2 => 반올림 법칙에 따라 그대로 놔두기
        ```
   2) NaN과 Infinity 확인
      * Number.isNaN(변수..) => 숫자가 아닌가?
        * 예시
          ```
          const m = Number('숫자 변환 불가')
          // m === NaN
          Number.isNaN(m) > true
          ```
        * 비교 연산자로 비교 불가
      * Number.isFinite(변수..) => 유한한 숫자인가?
        * 예시
          ```
          const n = 10/0 > 양의 무한대
          const o = -10/0 > 음의 무한대
          Number.isFinite(n) > false
          Number.isFinite(o) > false
          Number.isFinite(1) > true
          Number.isFinite(10) > true
          ```
        * 비교 연산자로 비교 가능
          ex) n === Infinity || n === -Infinity > true

5. String 객체
   1) trim(): 문자열 양쪽 끝의 공백(띄어쓰기, 줄바꿈 등) 없애기
      * 사용법: 문자열 이름.trim()
      * 예시
        ```
        stringA = '     안녕하셔유     '
        stringA.trim() > "안녕하셔유"
        ```
   2) split(): 특정 기호로 문자열을 잘라 "배열"로 리턴하는 메소드
      * 예시
      ```
      let input = `
      일자,달러,엔,유로
      02,1141.8,1097.46,1262.37
      03,1148.7, 1111.36,1274.65
      04,1140.6,1107.81,1266.58
      07,1143.4,1099.58,1267.8
      08,1141.6,1091.97,1261.07
      `
      input = input.trim() //앞뒤 공백 제거
      /*결과
      "일자,달러,엔,유로
      02,1141.8,1097.46,1262.37
      03,1148.7, 1111.36,1274.65
      04,1140.6,1107.81,1266.58
      07,1143.4,1099.58,1267.8
      08,1141.6,1091.97,1261.07"
      */
      input = input.split('\n') //줄바꿈으로 자르기
      /*결과
      ["일자,달러,엔,유로", "02,1141.8,1097.46,1262.37", "03,1148.7, 1111.36,1274.65", "04,1140.6,1107.81,1266.58", 
      "07,1143.4,1099.58,1267.8", "08,1141.6,1091.97,1261.07"]
      */
      input = input.map((line) => line.split(',')) //배열 내부 문자열들을 쉼표로 자름
      /*결과
      [Array(4), Array(4), Array(4), Array(4), Array(4), Array(4)]
      */
      ```
   => 이외 String 객체의 주요 속성: length, indexOf()


6. JSON 객체
   : 자바스크립트의 객체처럼 자료를 표현하는 방식으로, 각각의 프로그래밍 언어로
     만든 애플리케이션들이 데이터를 교환할 때 사용
   1) JSON 형식의 규칙
      * 값을 표현할 때 문자열, 숫자, 불 자료형만 사용 가능(함수 등은 사용 불가)
      * 문자열은 반드시 큰따옴표로 만들 것
      * key에도 반드시 따옴표를 붙여야함
   2) JSON.stringify(): JS객체 -> JSON 문자열
      * 예시
        ```javascript
        //자료 생성
        const data = [{
           name: '혼자 공부하는 파이썬',
           price: 18000,
           publisher: '한빛미디어'
        }, {
           name: 'HTML5 웹 프로그래밍 입문',
           price: 26000,
           publisher: '한빛아카데미'
        }]
        //자료를 JSON으로 변환
        console.log(JSON.stringify(data))
        console.log(JSON.stringify(data, null, 2))
        /*2번째 매개변수의 의미: 객체에서 어떤 속성만 선택해서 추출하고 싶을 때 사용함.
        그러나 거의 사용하지 않기에 일반적으로 null을 넣음*/
        //3번째 매개변수의 의미: 들여쓰기 n칸. 여기서는 2칸
        ```
        * 결과
          ```
          [{"name":"혼자 공부하는 파이썬","price":18000,"publisher":"한빛미디어"},{"name":"HTML5 웹 프로그래밍 입 
          문","price":26000,"publisher":"한빛아카데미"}]
          //두번째는 들여쓰기 2칸 추가됨
          [
            {
              "name":"혼자 공부하는 파이썬",
              "price":18000,
              "publisher":"한빛미디어"
            },
            {
              "name":"HTML5 웹 프로그래밍 입문",
              "price":26000,
              "publisher":"한빛아카데미"
            }
          ]
          ```
   3) JSON.parse(): JSON 문자열 -> JS 객체
      * 예시
        ```javascript
        //자료 생성
        const data = [{
           name: '혼자 공부하는 파이썬',
           price: 18000,
           publisher: '한빛미디어'
        }, {
           name: 'HTML5 웹 프로그래밍 입문',
           price: 26000,
           publisher: '한빛아카데미'
        }]
        //자료를 JSON으로 변환
        const json = JSON.stringify(data)
        console.log(json)
        //JSON 문자열을 다시 자바스크립트 객체로 변환
        console.log(JSON.parse(json))
      ```
      * 결과
      ```[{"name":"혼자 공부하는 파이썬","price":18000,"publisher":"한빛미디어"},{"name":"HTML5 웹 프로그래밍 입 
      문","price":26000,"publisher":"한빛아카데미"}]
      Array(2)
      0: {name: '혼자 공부하는 파이썬', price: 18000, publisher: '한빛미디어'}
      1: {name: 'HTML5 웹 프로그래밍 입문', price: 26000, publisher: '한빛아카데미'}
      length: 2
      __proto__: Array(0)
      ```
  => JSON의 메소드는 이렇게 JSON.stringify(), JSON.parse() 2가지뿐.

6. Math 객체
   1) Math.random(): 0 이상, 1미만의 숫자 랜덤 생성
      * 예시
        ```javascript
        const num = Math.random()
        console.log(num) // 0 이상 1 미만 숫자 랜덤 생성
        console.log(num * 10) // 0 이상 10 미만 숫자 랜덤 생성
        console.log(num * 50 - 25) // -25 이상 25 미만 숫자 랜덤 생성
        ```
   => 이외에도 Math.PI, Math.E 등 다양한 속성 속성 및 메소드 존재

7. 외부 script 파일 읽어들이기
   : 프로그램의 규모가 커지만 파일을 분리하는 게 좋음. 이런 상황에서 사용하는 기법
   1) 예시
      ```html
      <!DOCTYPE html>
      <html>
      <head>
         <title></title>
         <script src = "test.js"></script>
      </head>
      </html>
      ```

8. Lodash 라이브러리: 다른 사람이 만든 외부 JS파일 사용하기
   * lodash 라이브러리 다운로드 페이지: https://lodash.com
   * Lodash 라이브러리의 문서: https://lodash.com/docs/4.17.15
   1) 예시: sortBy()
      -> 지정한 기준을 기반으로 배열 정렬 후 리턴하는 메소드
      ```javascript
      <script src = "https://cdn.jsdelivr.net/npm/lidash@4.17.21/lodash.min.js">
      </script>
      <script>
        // 데이터 생성
        const data = [{
           name: '혼자 공부하는 파이썬',
           price: 18000,
           publisher: '한빛미디어'
        }, {
           name: 'HTML5 웹 프로그래밍 입문',
           price: 26000,
           publisher: '한빛아카데미'
        }, {
           name: '머신러닝 딥러닝 실전 개발 입문',
           price: 30000,
           publisher: '위키북스'
        }, {
           name: '딥러닝을 위한 수학',
           price: 25000,
           publisher: '위키북스'
        }]
        // 가격으로 정렬한 뒤 출력
        const output = _.sortBy(books, (book) => book.price)
        console.log(JSON.stringify(output, null, 2))
        // 가격이 낮은 순으로 출력된다
      </script>
      ```
