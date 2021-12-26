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
  ```
  시작  - [ 7 8 5 5 4 ]
  1번째 - [ 7 8 5 5 4 ]
  2번째 - [ 5 7 8 5 4 ]
  3번째 - [ 5 5 7 8 4 ]
  4번째 - [ 4 5 5 7 8 ]
  ```
  
* 선택 정렬
  * 첫 항목부터 자신 이후의 항목중 최솟값/최댓값을 찾아 그 항목과 자신을 바꾸어 가장 작은/큰 항목을 앞에서부터 순서대로 옮기는 방법
  
  ```
  package task;

  import java.util.Random;

  public class Task02 {
	  public static void main(String[] args) {
      int data[] = new int[5];
      Random rand = new Random();

      for (int i = 0; i < data.length; i++) {
        data[i] = rand.nextInt(9) + 1;
      } // 랜덤 배열 생성
		
      // 1차 출력
      System.out.print("시작  - [ ");
      for (int v : data) {
        System.out.print(v + " ");
      }
      System.out.println("]");
		
      for (int i = 0; i < data.length-1; i++) {//마지막 자리는 할 필요가 없다
        int minNum = i;
        int j;
        for (j = i+1; j < data.length; j++) {//자신 이후 항목들중 최소값을 찾는다
          if(data[j]<data[minNum]) {//크기 비교
          minNum = j;//가장 작은 인덱스 번호
        }
      }
      int tmp = data[i]; //자리 교체
      data[i] = data[minNum];
      data[minNum] = tmp;
			
      // i회 진행할때마다 출력
      System.out.print((i+1) + "번째 - [ ");
      for (int v : data) {
        System.out.print(v + " ");
      }
      System.out.println("]");
      }		
    }
  }
  ```
  
  
  * 해당 코드를 구현한 결과물
  ```
  시작  - [ 9 5 8 3 3 ]
  1번째 - [ 3 5 8 9 3 ]
  2번째 - [ 3 3 8 9 5 ]
  3번째 - [ 3 3 5 9 8 ]
  4번째 - [ 3 3 5 8 9 ]
  ```
