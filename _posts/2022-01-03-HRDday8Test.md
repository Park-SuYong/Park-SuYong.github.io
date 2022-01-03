---
2layout: single
title:  "소프트웨어 개발 및 응용과정 Day8 Test"
categories:
  - 소프트웨어 개발 및 응용과정
---

## Day8 Test

```
package Task;

import java.util.Random;

class Player {//기본생성자
	void game(Monster mon) {
		mon.attack();// Monster 클래스의 attack함수를 불러온다
	}

	void show(Monster mon) {
		mon.infor();// Monster 클래스의 infor함수를 불러온다
	}
}

class Monster {
	String name;
	int lv;

	Monster(String name) {
		this(name, 5);// Lv을 입력하지 않으면 디폴트값으로 5 지정
	}

	Monster(String name, int lv) {
		this.name = name;
		this.lv = lv;
	}

	void attack() {
		System.out.println(name + "의 공격!");//공격 선언
	}

	void infor() {
		System.out.println("이름: " + name + "   Lv : " + lv);//정보 보기
	}
}

class Pika extends Monster { // Monster 클래스를 상속
	Pika(int lv) {
		super("피카츄", lv);//특정 포켓몬들은 이름 고정
	}

	Pika() {// 오버로딩
		super("피카츄");//부모의 생성자
	}

	void attack() {// 다형성, 오버라이딩, 재정의
		super.attack();
		System.out.println("백만볼트!");// 기술 이름을 추가로 출력
		lv++;// Lv 1 증가
	}
}

class Pai extends Monster {
	Random rand = new Random();

	Pai(int lv) {
		super("파이리", lv);
	}

	Pai() {
		super("파이리");
	}

	void attack() {
		super.attack();
		System.out.println("불대문자!");
		lv += (rand.nextInt(5) + 1);// Lv 1~5 랜덤하게 증가
	}
}

public class Test01 {

	public static void main(String[] args) {
		Player player = new Player(); // 플레이어 생성
		Monster[] mon = new Monster[2];// 몬스터 자리 2개
		mon[0] = new Pika();// 피카추는 기본Lv
		mon[1] = new Pai(10);// 파이리는 10Lv
		for (int i = 0; i < mon.length; i++) {// 초기 포켓몬들의 정보
			player.show(mon[i]);
		}
		for (int i = 0; i < 2; i++) {// 전투를 2회씩 실행
			for (int j = 0; j < mon.length; j++) {
				player.game(mon[j]);
			}
		}
		for (Monster1 v : mon) {// 전투 후 정보
			player.show(v);
		}
	}
}
```

* 실행결과

```
이름: 피카츄   Lv : 5//시작시 정보
이름: 파이리   Lv : 10
피카츄의 공격!
백만볼트!
파이리의 공격!
불대문자!
피카츄의 공격!
백만볼트!
파이리의 공격!
불대문자!
이름: 피카츄   Lv : 7//피카츄는 공격시마다 +1
이름: 파이리   Lv : 18//파이리는 공격시마다 랜덤하게 증가
```

