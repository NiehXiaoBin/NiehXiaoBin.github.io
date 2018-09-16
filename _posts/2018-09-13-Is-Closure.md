---
layout: post
title: Is Closure ?
categories: [Java, Lambda]
description: This is a closure ?
keywords: Java, closure
---

## Is Closure ?

1. 
    1. code
    
        ```java
        public class Closure {
            
            static Integer num = 0;
            
            static void sayHello() {
                System.out.println(num++ + " Hello World");
            }
            
            public static  void main(String ... args){
        
                Runnable task = Closure::sayHello;
        
                System.out.println(task.getClass());
        
                for (int i = 0; i < 5; i++) {
                    Closure.sayHello();
                }
        
                for (int i = 0; i < 5; i++) {
                    task.run();
                }
        
                System.out.println(num);
            }
        }
        ```
     
    1. out 
    
        > 0 Hello World  
          1 Hello World  
          2 Hello World  
          3 Hello World  
          4 Hello World  
          5 Hello World  
          6 Hello World  
          7 Hello World  
          8 Hello World  
          9 Hello World  
          10
          
1. 
    1. code
        ```java
        public class Closure {
        
            static List<Runnable> getTask() {
                List<Runnable> list = new ArrayList<>();
                for (AtomicInteger num = new AtomicInteger(); num.get() < 3; num.incrementAndGet()) {
                    list.add(() -> System.out.println(num.get() * num.get()));
                }
                return list;
            }
        
        
            public static void main(String[] args) {
                List<Runnable> taskList = getTask();
                taskList.forEach(Runnable::run);
            }
        
        }
        ```
    1. out
        > 9  
          9  
          9

1. 
    1. code
        ```javascript
           function getTask() {
               var list = [];
               for (var i = 0; i < 3; i++) {
                   list.push(function () {
                       return i * i;
                   });
               }
               return list;
           }
           
           getTask().forEach(task => console.log(task()));
        ```
    1. out
        > 9  
          9  
          9