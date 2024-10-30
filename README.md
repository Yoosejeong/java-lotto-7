# 📃로또
## 기능 요구 사항
간단한 로또 발매기를 구현한다.  
### 로또
* 로또 번호의 숫자 범위는 1~45까지이다.
* camp.nextstep.edu.missionutils.Randoms의 pickUniqueNumbersInRange()을 활용하여 랜덤으로 중복되지 않는 6개의 숫자로 이루어진 로또를 발매한다.
* 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.  
1등: 6개 번호 일치 / 2,000,000,000원  
2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원  
3등: 5개 번호 일치 / 1,500,000원  
4등: 4개 번호 일치 / 50,000원  
5등: 3개 번호 일치 / 5,000원
* 주어진 로또 클래스를 활용한다.
* 단, Lotto에 numbers 이외의 필드(인스턴스 변수)를 추가할 수 없으며, numbers의 접근 제어자인 private은 변경할 수 없다.
```java
public class Lotto {
    private final List<Integer> numbers;

    public Lotto(List<Integer> numbers) {
        validate(numbers);
        this.numbers = numbers;
    }

    private void validate(List<Integer> numbers) {
        if (numbers.size() != 6) {
            throw new IllegalArgumentException("[ERROR] 로또 번호는 6개여야 합니다.");
        }
    }

    // TODO: 추가 기능 구현
}
```

### 입력
* 로또 구입 금액을 입력받는다.
* 로또 구입 금액은 1000원 단위로 가능하며, 아닐시엔 IllegalArgumentException을 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
* 당첨 번호로 중복되지 않는 숫자 6개와 보너스 번호를 1개를 입력받는다.
### 출력
* 사용자가 구매한 로또의 개수를 출력한다.
* 사용자가 구매한 로또의 개수만큼 로또 번호를 모두 출력한다.
* 사용자의 로또와 당첨 번호를 비교하여 당첨 내역을 출력한다.
* 수익률 출력 후 로또 게임을 종료한다.
## ⭐기능 목록
1. 사용자로부터 로또 금액을 입력 받는 메서드
2. 입력받은 로또 금액에 맞게 로또를 랜덤으로 발행하는 메서드
3. 발행 받은 로또들 출력하는 메서드
4. 당첨번호를 입력 받는 메서드
5. 보너스 번호를 입력 받는 메서드
6. 사용자의 로또와 당첨번호를 비교하는 메서드
7. 당첨 내역 출력하는 메서드
8. 수익률 구하는 메서드
9. 수익률 출력하는 메서드
## 🚨에러
### 로또 금액 입력받는 경우
* 사용자로부터 입력받은 로또 금액이 1000 단위가 아닐 경우
### 로또 번호, 보너스 번호 입력 받는 경우
* 로또 번호와 보너스 번호를 1~45 사이로 입력받지 않았을 경우
* ,가 아닌 다른 구분자를 사용했을 경우
* 로또 번호에 중복된 숫자를 입력 받는 경우
* 보너스 번호가 하나가 아닐 경우
## 입출력 요구 사항
### 입력
* 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
14000
* 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.
1,2,3,4,5,6
* 보너스 번호를 입력 받는다.
7
### 출력
* 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.
8개를 구매했습니다.  
[8, 21, 23, 41, 42, 43]  
[3, 5, 11, 16, 32, 38]  
[7, 11, 16, 35, 36, 44]  
[1, 8, 11, 31, 41, 42]  
[13, 14, 16, 38, 42, 45]  
[7, 11, 30, 40, 42, 43]  
[2, 13, 22, 32, 38, 45]  
[1, 3, 5, 14, 22, 45]  
* 당첨 내역을 출력한다.
3개 일치 (5,000원) - 1개  
4개 일치 (50,000원) - 0개  
5개 일치 (1,500,000원) - 0개  
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개  
6개 일치 (2,000,000,000원) - 0개  
* 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
총 수익률은 62.5%입니다.
* 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.
[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
### 실행 결과 예시
구입금액을 입력해 주세요.  
8000  
  
8개를 구매했습니다.  
[8, 21, 23, 41, 42, 43]  
[3, 5, 11, 16, 32, 38]  
[7, 11, 16, 35, 36, 44]  
[1, 8, 11, 31, 41, 42]  
[13, 14, 16, 38, 42, 45]  
[7, 11, 30, 40, 42, 43]  
[2, 13, 22, 32, 38, 45]  
[1, 3, 5, 14, 22, 45]  
   
당첨 번호를 입력해 주세요.  
1,2,3,4,5,6  
  
보너스 번호를 입력해 주세요.  
7  
  
당첨 통계  
---  
3개 일치 (5,000원) - 1개  
4개 일치 (50,000원) - 0개  
5개 일치 (1,500,000원) - 0개  
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개  
6개 일치 (2,000,000,000원) - 0개  
총 수익률은 62.5%입니다.  
