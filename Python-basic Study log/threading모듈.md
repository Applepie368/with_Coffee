2026.03.22 (일)

💿 'threading 모듈'

약간의 부록 느낌으로 예시를 통해 배운거다. 내가 직접 쓴 코드는 아니고, 이 코드로 이해를 하였다.

일단 thread는 '실'이라는 단어인데, 여러개의 실로 뻗어나간다는 의미라고 하는 것 같다.

다음은 완성된 예시이다.


```python
import time 
import threading

def long_task():
  for i in range(5):
    time.sleep(1)    #출력하는 시간 간격을 1초로 설정
    print("working: %s\n" % i)

print("Start")

threads = []
for i in range(5):    #사실 i변수는 해당 반복문에서 쓰지 않고, 단순 몇 번 반복을 하기 위해서 넣는 안쓰는 변수, 그럴 때는 관례적으로 _를 변수로 쓴다고 한다
  t = threading.Thread(target=long_task)    #thread를 만들건데, long_task라는 함수를 이용하는 thread, 그걸 변수 t에 저장
  threads.append(t)    #thread라는 빈 리스트에 t를 저장, 그걸 5번 하는데, t가 중복되는게 아니라 다른 t임
for t in threads:
  t.start()    #스레드 시작시키는 메서드
for t in threads:
  t.join()    #스레드가 끝날 때까지 다른 것들이 기다리게 하는 메서드

print("End")
```


우선 threads라는 빈 리스트에 뭐가 들어갔는지가 궁금했다. 그래서 이 예시 맨 밑에 print(threads)를 했더니, working: 0 이런게 아니라 스레드를 통해 만들어진 객체들이 빼곡했다.

그걸 __str__로 변형을 해야한다고는 하는데, 일단 넘어갔고, 그 객체의 의미가 처음 thread 반복문에서 5번의 t를 각각 다르게 인식하고 받아들였다는 것은 이해했다.

그렇게 다 리스트에 들어오면 대기하다가, 마치 달리기 시합처럼 준비, 출발을 start()라는 메서드가 해주면, 그 안의 서로 다른 t들이 동시에 움직이는 것이다(즉, 위의 long_task()함수 실행)

근데 .join을 안쓰면 밑에 print() 함수의 결과가 threads를 작동시키는 중에 동시에 작동된다, 그래서 후순위에 배치된 코드들은 잠시 대기하라고 꼭 써줘야 한다고 한다.

지금 코드를 보면 threads 본체 -> start 메서드 -> join 메서드 순으로 되어있다. 근데 궁금한게 순서가 달라지면 안되나 싶었다.

결과적으로 말하면 안된다. 각각 예시와 결과로 보여주겠다. 안되는건 아닌데 threads 끝나고 print()가 발생하는 그림은 아니다.


```python
threads = []
for i in range(5):    
  t = threading.Thread(target=long_task)    
  threads.append(t)    

#print("End") 위치시 start가 아직 작동 안해서 End 먼저 출력 후 threads 작동

for t in threads:
  t.start()   

#print("End") 위치시 join가 아직 작동 안해서, threads 중간에 End 출력

for t in threads:
  t.join()   

print("End")    #threads 모두 작동 끝나고, End 출력 -> 우리가 생각한 그림
```


동시에 프로그램을 작동시킨다는게 흥미로운데, claude에게 물어보니 다른 걸 더 쓴다고 한다는데.. 훔.. 

어쨌건 순서도 중요하고, 여러가지 신경쓸게 좀 많은 것 같다
