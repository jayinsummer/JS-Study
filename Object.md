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
