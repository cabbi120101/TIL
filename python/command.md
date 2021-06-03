# 파이썬

> 기본 문법 정리



### 함수

- 기본 형태

  ```python
  def my_func(a):
    b = a + 10
    print("결과:",b)
    print("My first function")
  ```

  ```python
  def my_func(a,b,c):
    d = a + b + c
    return d
  ```



### class 

- Bicycle class 만들어보기

  ```python
  class Bicycle():
    
    
    def move(self,speed):
      print("자전거: 시속 {0}킬로미터로 전진".format(speed))
      
    def turn(self, direction):
      print("자전거: {0}회전".format(direction))
      
    def stop(self):
      print("자전거({0},{1}): 정지".format(self.wheel_size,self.color))
  ```

  