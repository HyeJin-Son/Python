## class 의 self 개념 이해

1. **클래스의 구조**

```
class UserName: #유저의 자료형
    멤버 변수 선언
    메서드
```
ex)합을 구하는 클래스
```python
class U_class : #
    a=0
    b=0

    def Hap(self, a,b)
        self.a=a
        self.b=b
        return self.a+self.b
```

2. **self 개념 이해**
- 메소드 매개인자로 첫인자는 클래스의 주소를 가지는 의미로 self를 명시함
- 메서드 호출 시 self는 따로 전달하지 않아도 됨.
- ex) 합을 구하는 클래스
```python
class U_class : 
    a=0
    b=0

    def Hap(self, a,b)
        self.a=a
        self.b=b
        return self.a+self.b

u1=U_class() # u1 인스턴스 생성
print(u1.Hap(100,200)) #결과 300출력

u2=U_class() # u2 인스턴스 생성
print(u2.Hap(5,20)) #결과 25출력
```
- u1.Hap(100,200)이 실행되면 self에는 u1이 전달되고 self.a를 통해 u1이 가진 a의 정보에 접근할 수 있다는 의미이다. 
 
