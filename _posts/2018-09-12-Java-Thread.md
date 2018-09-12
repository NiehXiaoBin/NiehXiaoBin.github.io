---
layout: post
title: Java Thread
categories: [Java, Thread]
description: 读书笔记
keywords: Java, Thread
---
Thread 
---
## 1. ready
```java
    // 模拟一个比较耗时的操作
    public static void sayHello() {
        String hello = "Hello World\n";
        char[] charArray = hello.toCharArray();
        for (char ch : charArray) {
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.print(ch);
        }
    }
```
## 1. new
1. 继承 Thread 重写 run 方法 
    ```java
        Thread task = new Thread(){
            @Override
            public void run() {
                sayHello();
            }
        };
    ```
1. 实现 Runnable 接口，将实现类对象作为参数传递给 Thread 的构造方法
    ```java
        Runnable runnable = new Runnable() {
            @Override
            public void run() {
                sayHello();
            }
        };
        Thread thread = new Thread(runnable);
    ```
## 1. run 
1. 运行
    ```java
        public static void main(String[] args) {
            task.run();
            System.out.println("End");
        }
    ```
1. 输出
    > Hello World  
    End
1. Thread 的 run
    ```java
        public class Thread implements Runnable {
            private Runnable target;
            
            ...
            
            public Thread(){};
            public Thread(Runnable target){
               ...
               this.target = target;
               ... 
            }
            
            @Override
            public void run(){
                if(target != null){
                    target.run();
                }
            }
        }
    ```
1. run 只是个普通的方法

## 1. start
1. 运行
    ```java
        public static void main(String[] args) throws InterruptedException {
            task.start();
            System.out.println("End");
            task.join();
        }
    ```
1. 输出
    > End  
    Hello World
    