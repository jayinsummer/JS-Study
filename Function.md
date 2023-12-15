## 익명함수
1. 말 그대로 "이름이 없는 함수"
2. 사용방식
   ```javascript
   const Hamsu = function(){
      ...
   }
   //호출
   Hamsu()
   ```

## 선언적 함수
1. 이름이 있는 함수
2. 사용방식
   ```javascript
   function Hamsu(){
     ...
   }
   //호출
   Hamsu()
   ```

## 나머지 매개변수
1. 가변 매개변수 함수: 매개변수의 개수가 고정적이지 않은 함수
   -> 이때 "나머지 매개변수" 활용
2. 사용방식: 매개변수 앞에 마침표 3개(...)
   ```javascript
      function sample(...items){
          console.log(items
      }
      sample(1,2,3)
      sample(1,2,3,4)```
  
## 전개 연산자
1. 매개변수에 배열을 입력할 수 없고, *숫자만* 가능한 경우 사용
2. 배열을 전개해서 함수의 매개변수로 전달해줌
3. 사용방식: *배열* 앞에 마침표 3개(...)
   ```javascript
   function sample(...items){
       console.log(items)
   }

   const array = [1,2,3,4]

   console.log('전개 연산자 사용 안함')
   sample(array) //결과: [Array(4)] -> 4개의 요소가 들어있는 배열이 들어왔음
   console.log('전개 연산자 사용')
   sampe(...array) //결과: [1,2,3,4]
   ```

   ## 기본 매개변수
   1. 매개변수에 기본값 지정
   2. 주의: 매개변수 맨 오른쪽부터 채울 것
      ex) function(a, b=기본값) (X)
          function(a=기본값, b) (O)
   3. 사용 방식
      ```javascript
      function earnings(name, wage=8590, hours=40){
          ...
      }
      ```
      => wage와 hours에 특별한 인자를 전달하지 않으면, 기본값으로 계산됨

   ## 배열 타입 확인하는 법
   1. 숫자 타입: typeof()
      ex) typeof(num) === 'number'
   2. 배열 타입: Array.isArray(배열)
      * typeof(배열) === 'object' 와 같은 방식으로 확인 가능하긴 하지만 위 방식이 더 정확!
