---
2layout: single
title:  "소프트웨어 개발 및 응용과정 Day7 Test"
categories:
  - 소프트웨어 개발 및 응용과정
---

## Day7 Test

* Day7 테스트 - 복권 만들기
  * 복권의 번호는 중복되지 않는다
  * 0이하의 입력을 방지해라
  * 같은 숫자가 있으면 1개당 1점 - 3점이 넘어가면 당첨

```
package exam;

import java.util.Random;
import java.util.Scanner;

public class Task01 { 
	public static int check(int data[], int user[]) {//비교하는 함수
		int score = 0;// 점수
		int cnt = 0;// 당첨 여부
		for (int i = 0; i < data.length; i++) {
			for (int j = 0; j < user.length; j++) {
				if (data[i] == user[j]) {
					score++;// 같은게 있을때마다 점수를 +해준다
				}
			}
		}
		show(user);// 출력
		System.out.println(" : " + score + "점");// 이번엔 점수까지
		if (score >= 3) {// 3점 이상이면
			cnt++;// 당첨 1회
		}
		return cnt; // 리턴
	}

	public static void show(int data[]) {// 복권의 각 항목을 보여준다
		System.out.print("[ ");
		for (int v : data) {
			System.out.print(v + " ");
		}
		System.out.print("]");
	}

	public static void makeLott(int[] lott, int lottSize, int lottNum) {
		Random rand = new Random();// 랜덤한 복권을 생성해준다
		int cnt = 0;// 몇번째 항목인지
		while (cnt < lottSize) {// 배열의 사이즈를 넘지 않게
			boolean res = false;
			lott[cnt] = rand.nextInt(lottNum) + 1;// 랜덤 숫자 부여
			if (cnt > 0) {// 0번째는 비교할 대상이 없다
				for (int i = 0; i < cnt; i++) {// 각 항목과 비교 시작
					if (lott[i] == lott[cnt]) {// 같은게 있으면
						res = true;// if문을 활성화
					}
				}
			}
			if (res) {
				continue;// 다시
			}
			cnt++;// res가 ture로 바뀌지 않았다면 다음 항목으로
		}
	}

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int lottSize = 5;// 복권의 항목 수
		int data[] = new int[lottSize];// 당첨번호
		int user[] = new int[lottSize];// 유저가 산 번호
		String buy;// 살지 여부
		int buyNum;// 몇장인지
		int cnt;// 당첨 횟수
		int lottNum = 45;// 숫자의 최댓값

		while (true) {// 반복
			System.out.print("복권을 주문하시겠습니까? : ");
			buy = sc.next();
			if (buy.equalsIgnoreCase("yes")) {// yes라면(대소문자 구분 없이)

				makeLott(data, lottSize, lottNum);// 당첨번호를 만들어준다
				do {// 일단 1번은 실행
					System.out.print("몇장을 구매하시겠습니까?(10~1장) : ");
					buyNum = sc.nextInt();
				} while (buyNum <= 0 || buyNum > 10);// 범위에서 벗어났다면 다시 실행
				System.out.print("당첨 번호는 ");
				show(data);
				System.out.println(" 입니다"); // 당첨번호 출력
				cnt = 0;
				for (int i = 0; i < buyNum; i++) {// 구매한 장수 만큼
					makeLott(user, lottSize, lottNum);// 랜덤한 유저 복권을 만들고
					cnt += check(data, user);// check 함수를 통해 당첨 횟수를 측정하고 결과를 보여준다
				}
				if (cnt == 0) {// 당첨 횟수가 0이라면 출력
					System.out.println("당첨 0회 아쉽습니다");
				} else// 아니라면
					System.out.println("당첨 " + cnt + "회 축하합니다");
				System.out.print("한번 더 "); // 구매가 끝난 후 재구입 의사를 물어보며 while의 첫 부분으로 복귀
			} else if (buy.equalsIgnoreCase("no")) {// no입력시 종료
				System.out.println("행복한 하루 되세요");
				break;
			} else {// yes도 no도 아니라면 다시
				System.out.println("잘못된 입력을 하셨습니다");
			}
		}
	}
}
```

* 실행 결과

```
복권을 주문하시겠습니까? : YEs
몇장을 구매하시겠습니까?(10~1장) : 10
당첨 번호는 [ 26 37 7 11 4 ] 입니다
[ 42 23 33 25 11 ] : 1점
[ 24 19 43 7 16 ] : 1점
[ 26 18 12 29 17 ] : 1점
[ 39 44 26 11 37 ] : 3점
[ 17 13 10 37 43 ] : 1점
[ 20 27 44 42 16 ] : 0점
[ 13 27 6 16 1 ] : 0점
[ 44 32 31 36 19 ] : 0점
[ 1 40 8 5 36 ] : 0점
[ 41 29 32 12 13 ] : 0점
당첨 1회 축하합니다
한번 더 복권을 주문하시겠습니까? : yes
몇장을 구매하시겠습니까?(10~1장) : 3
당첨 번호는 [ 10 20 42 2 44 ] 입니다
[ 3 2 18 35 21 ] : 1점
[ 5 21 45 34 7 ] : 0점
[ 7 14 40 22 42 ] : 1점
당첨 0회 아쉽습니다
한번 더 복권을 주문하시겠습니까? : ys
잘못된 입력을 하셨습니다
복권을 주문하시겠습니까? : no
행복한 하루 되세요
```

