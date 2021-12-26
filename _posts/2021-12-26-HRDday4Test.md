---
layout: single
title:  "소프트웨어 개발 및 응용과정 Day4 Test"
categories:
  - 소프트웨어 개발 및 응용과정
---
## Day4 과제

* 삽입 정렬
  * 배열의 모든 요소를 자신의 앞 항목들과 하나씩 비교해서 자신이 들어가야 할 자리를 찾아 해당 자리로 들어가고 이후의 항목을 한칸씩 미루는 방식
  ```
  package task;

  import java.util.Random;

  public class Task01 {
    public static void main(String[] args) {
    int data[] = new int[5];
    Random rand = new Random();
		
    for (int i = 0; i < data.length; i++) {
      data[i] = rand.nextInt(10)+1;
    }//랜덤 배열 생성

    //1차 출력
    System.out.print("시작  - [ ");
    for (int v : data) {
      System.out.print(v + " ");
    }
    System.out.println("]");
		
    for (int i = 1; i < data.length; i++) { //2번째 자리부터 시작
      int tmp = data[i]; //비교할 대상 고정
      int j = i-1; //대상의 이전 번째부터 비교
      while(j>=0&&data[j]>tmp) {//data[i] 와 그 앞 항목 비교
        data[j+1] = data[j];//비교해서 크면 해당 숫자를 1칸 뒤로
        j--;//비교하는 자리를 한칸씩 앞으로
      }
      data[j+1] = tmp;//비교하던 대상을 마지막으로 while문이 T였던 자리로
			
      //i회 진행할때마다 출력
      System.out.print(i + "번째 - [ ");
      for (int v : data) {
        System.out.print(v + " ");
      }
      System.out.println("]");
      }
    }
  }
  ```
  * 해당 코드를 구현한 결과물
  
  시작  - [ 7 8 5 5 4 ]
  1번째 - [ 7 8 5 5 4 ]
  2번째 - [ 5 7 8 5 4 ]
  3번째 - [ 5 5 7 8 4 ]
  4번째 - [ 4 5 5 7 8 ]
  
