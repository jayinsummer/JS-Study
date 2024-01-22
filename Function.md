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
     
   ## 콜백 함수
   1. 매개변수로 전달하는 함수
   2. 사용방식(1) - 선언적 함수
      ```javascript
      function callThreeTimes (callback){
         for(let i=0; i<3;i++){
            callback(i)
         }
      }

      function print(i){
         console.log(`${i}번째 함수 호출`)
      }

      callThreeTimes(print)
      ```
   3. 사용방식(2) - 익명함수
      ```javascript
      function callThreeTimes (callback){
        for(let i=0; i<3; i++){
            callback(i)
        }
    }

    callThreeTimes(function(i){
        console.log(`${i}번째 함수 호출`)
    })
      ```
      => 익명함수에서는 함수를 따로 선언하지 않고 바로 작성함
   4. 콜백함수를 활용하는 함수(1): forEach()
      1) 배열의 함수 메소드-배열 내부 요소를 사용해서 콜백함수 호출
      2) 형태: function (value, index, array) {}
      3) 사용법: 배열이름.forEach(function(value, index, array){...})
      4) 예시
      ```javascript
      const numbers = [273, 52, 103, 32, 57]

      numbers.forEach(function(value, index, array){
        console.log(`${index}번째 요소 : ${value}`)
      })
      /*
      <결과>
      0번째 요소 : 273
      1번째 요소 : 52
      2번째 요소 : 103
      3번째 요소 : 32
      4번째 요소 : 57
      */
      ```
   5. 콜백함수를 활용하는 함수(2): map()
      1) 콜백함수에서 리턴한 값들을 기반으로 새로운 배열을 만드는 함수
      2) 사용법: 배열 = 배열.map(function(value, index, array){..})
         -> 이런 식으로 배할당해주지 않으면 기존 배열은 변하지 않는다.
      3) 예시
         ```javascript
         let numbers = [273, 52, 103, 32, 57]
         numbers = numbers.map(function(value){
            return value*value
         })

         numbers.forEach(console.log)
         ```
         *위 예시처럼 콜백함수에 매개변수 value, index, array 3개 모두 입력할 필요 없음.
          사용하고자 하는 위치의 것만 순서에 맞춰 입력하면됨.
   6. 콜백함수를 활용하는 함수(3): filter()
      1) 사용법: 배열 = 배열.filter(function(value){..})
         -> 얘도 이런 식으로 재할당 해줘야함
      2) 예시
         ```javascript
         const numbers = [0, 1, 2, 3, 4, 5]
         const evenNumbers = numbers.filter(function(value){
            return value % 2 === 0
         })

         console.log(`원래 배열: ${numbers}`)
         console.log(`짝수만 추출: ${evenNumbers}`)
         ```

   ## 화살표 함수
   1. "function" 키워드 대신 화살표(=>) 사용
   2. 사용법: (매개변수) => {}
   3. 예시
      ```javascript
      let array = [0,1,2,3,4,5,6,7,8,9]

      array = array.map((value)=>value*value)
      console.log(array)
      ```
   ## 타이머 함수
   1. setTimeout(함수, 시간): 특정 시간 후에 함수를 한 번 호출
      1) 예시
         ```javascript
         setTimeOut(()=>{
            console.log('1초 후에 실행됩니다')
         }, 1*1000)
         ```
   2. setInterval(함수, 시간): 특정 시간마다 함수 호출
      1) 예시
         ```javascript
         setInterval(()=>{
            console.log(`1초마다 실행됩니다(${count}번째)`)
            count++
         }, 1*1000)
         ```
   3. clearTimeout(타이머_ID): setTimeout() 함수로 설정한 타이머 제거
   4. clearInterval(타이머_ID): setInterval() 함수로 설정한 타이머 제거_
      1) 예시
         ```javascript
         let id
         let count = 0
         id = setInterval(()=>{
           console.log(`1초마다 실행됩니다(${count}번째)`)
           count++
         }, 1*1000) //1초마다 메시지 출력

         setTimeout(()=>{
           console.log('타이머를 종료합니다.')
           clearInterval(id)
         }, 5*1000) //5초 후에 타이머 종료
         ```

   ## 더 알아보기
   1. 변수 충돌 막기
      1) 블록 및 함수블록 사용
         * 최신 자바스크립트에서는 모두 가능하지만 구 버전에서는 __함수블록__만 가능
   2. 엄격 모드
      1) 블록 가장 위쪽에 'use strict' 작성하여 코드 엄격 검사
