
##코드 작성 후 review

1. 제공된 데이터를 이용하여 웹서버 로그(본 페이지 수, 서비스를 요청한 페이지수)를 처리하는 코드를 작성하시오.
웹서버로그 : 상태값이 200일떄 ++
   - tip) readLine()으로 읽어서 split() 함 -> 8번째 인덱스 =='200'

```python
datalist=[] 
with open('access_log.txt', 'r') as f:

        while True:
            data=f.readline() #한줄씩만 출력함
            if not data: break

            #print(data) #data 한줄로 받아오는 것 확인
            else datalist.append(data.strip().split())
        print((datalist)) #내용 리스트로 저장


log=0 # 웹서버로그
for d in range(len(datalist)) :
    if datalist[d][8] == '200':
        log +=1

print(f'웹 서버로그 상태 값이 200인 갯수 : ', log)
```

2. 제공된 데이터를 이용하여 웹서버 방문자 수를 계산하는 코드를 작성하시오.(동일한 IP를 갖는 클라이언트가 웹 사이트에 여러 번 접속하더라도 한 사람이 방문한 것으로 계산할 것.)
    - tip) 웹서버 방문자 : 다 스플릿 후 0번쨰 인덱스

```python
visitor=[] # 웹서버 방문자
visitor02=[]# 중복 ip 제거 후 저장할 리스트

for d in range(len(datalist)) :

    visitor.append(datalist[d][0])

    for x in visitor:
        if x not in visitor02: # not in.. visitor02에 값이 없으면 값 추가
            visitor02.append(x)

print(f'웹서버 방문자 방문 횟수(중복 제거):',len(visitor02))

```


3. 제공된 데이터를 이용하여 웹서버 총 서비스한 데이터의 용량을 계산하는 코드를 작성하시오. (계산 단위는 KB로 함.)
    - tip) 총 서비스한 데이터 용량 : 스플릿 후 9번쨰 index + 

```python
tot =0#총 서비스한 데이터 용량
for d in range(len(datalist)) :

    if datalist[d][9].isdigit():# 숫자 문자열만 받아오는 isdigit()
        tot += int(datalist[d][9])


print(f'총 서비스한 데이터 용량 :  {tot} KB')

```

4. 제공된 데이터를 이용하여 웹서버의 특정 사용자에게 서비스한 데이터의 용량을 계산하는 코드를 작성하시오
    - tip) 0번지 인덱스, 9번쨰 인덱스 

```python
Tot = 0;
print(f'-----------특정 사용자에게 서비스한 테이터의 용량-------------')
for i in visitor02 :#중복되는 ip 제거한 것


            for k in range(len(datalist)):

                if i==datalist[k][0] :

                    if datalist[k][9].isdigit():  # 숫자 문자열만 받아오는 isdigit()
                        Tot += int(datalist[k][9])
                else :
                    pass

            print(f'{i} 사용자에게 서비스한 데이터의 용량은 : {Tot} KB 입니다.')

```

## **정리**

1. 새로 알게된 내용
   - 중복 체크 : for 문으로 not in을 사용하여 중복체크를 함(순서 있음), set 함수로 중복체크 가능(순서없음->RUN 할때마다 순서바뀜)
   - isdigit() - 숫자문자열만 받아오는 함수





