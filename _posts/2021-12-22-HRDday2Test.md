---
layout: single
title:  "소프트웨어 개발 및 응용과정 Day2 Test"
categories:
  - 소프트웨어 개발 및 응용과정
---
## Day2 과제

* 문제풀이
  * 약수구하기
    ```
    import java.util.Scanner;

    public class Test01 {
      public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("약수를 구할 숫자를 입력하세요 : ");
        int num = sc.nextInt();
        for (int i = 1; i <= num; i++) {
          if(num%i==0) {
          System.out.print(i + " ");
          }
        }
      }
    }
    ```


  * 최대공약수 구하기
    ```
    import java.util.Scanner;

    public class Test02 {
      public static void main(String[] args) {
      Scanner sc = new Scanner(System.in);
      int max = 0;
      System.out.println("최대공약수 구하기");
      System.out.print("정수1 : ");
      int num1 = sc.nextInt();
      System.out.print("정수2 : ");
      int num2 = sc.nextInt();
      for (int i = num1; i >= 1; i--) {
        if (num1 % i == 0) {
          if (num2 % i == 0) {
            max = i;
            break;
            }
          }
        }
        System.out.println("최대공약수는 "+ max +"입니다");
      }
    }
    ```


  * 최소공배수 구하기
    ```
    import java.util.Scanner;
    
    public class Test03 {
      public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int min = 0;
        System.out.println("최소공배수 구하기");
        System.out.print("정수1 : ");
        int num1 = sc.nextInt();
        System.out.print("정수2 : ");
        int num2 = sc.nextInt();
        for(int i = num2; i>=1;i--) {
          if((num1*i)%num2==0) {
          min = (num1*i);
         }
        }
        System.out.println(min);
      }
    }
    ```
  * 소수 여부구하기
    
    import java.util.Scanner;
    
    public class Test04 {
      public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("소수인지 확인할 숫자를 입력하세요 : ");
        int num = sc.nextInt();
        for (int i = 2; i <= 10; i++) {
          if(num!=i) {
          if (num % i == 0) {
            System.out.println("소수가 아닙니다");
            break;
            }
          System.out.println("소수입니다");
          break;
         }
        }
      }
    }
    
  * 완전수 구하기
    
    public class Test05 {
      public static void main(String[] args) {
        System.out.println("완전수 구하기");
        for (int i = 1; i <= 1000; i++) {
          int num=0;
          for(int j = 1;j <i; j++ ) {
            if(i%j==0) {
            num += j;
            }
          }
           if(num==i) {
          System.out.println(num);
          }
        }
      }
    }
    

  * 369 게임
    
    public class Test06 {
      public static void main(String[] args) {
        System.out.println("369게임 시작");
          for(int i = 1; i <=100; i++) {
            int a = i%10;
            int b = i/10;
              if((a%3==0&&a!=0)||(b%3==0&&b!=0)) {
              System.out.print("짝 ");
             }else {
            System.out.print(i + " ");
           }
         }
       }
     }
    

  * 서로소 여부구하기
    
    import java.util.Scanner;
    
    public class Test07 {
      public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.print("정수1입력: ");
        int num1=sc.nextInt();
        System.out.print("정수2입력: ");
        int num2=sc.nextInt();
        if(num1>num2) {
          int tmp=num1;
          num1=num2;
          num2=tmp;
        }
        int ans=num1; // 서로소 판정을 위해 저장해야하는 최대공약수 공간
        for(int i=num1;i>=1;i--) {
          if(num1%i==0 && num2%i==0) {
            System.out.println("최대공약수는 "+i+"입니다.");
            ans=i;
            break;
           }
          }
          if(ans==1) {
            System.out.println("서로소입니다.");
          }else {
          System.out.println("서로소가 아닙니다.");
         }
       }
    }
    
