# JupyterNotebook, Jupyter lab 시작 폴더 위치 변경

상태: Not started
생성 일시: 2022년 10월 9일 오후 11:39
최종 편집 일시: 2022년 10월 18일 오전 11:05

![Untitled](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled.png)

컴퓨터를 포맷하는 김에 SSD 하나(F 드라이브)를 분석용 데이터와 파일을 저장하는 용도로 쓰기 위해 싹 비워 놨다. 

다시 아나콘다를 깔고 주피터를 들어가니 시작 폴더 위치가 ‘/C:/User/user’로 고정되어 생각치도 못 한 불편함이 발생했다. 

그래서 주피터 노트북, 주피터 랩 시작 폴더를 원하는 위치로 바꾸는 작업을 진행했고, 이왕 한 김에 블로그 첫 포스트로 작성해 본다.  

![root_dir 변경 전 주피터 노트북 시작(?) 위치](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%201.png)

root_dir 변경 전 주피터 노트북 시작(?) 위치

물론 프롬프트를 켜서 cd해서 원하는 위치까지 가서 주피터 노트북, 랩을 켜도 되지만 콘다 네비게이터를 사용하는 편이 훨씬 간편하므로 아예 시작 위치를 바꾸려고 찾아봤다.

```bash
(base) C:\Users\user>F:
(base) F:\>jupyter notebook
```

아래가 구글링+삽질로 해결한 내용이다. 

<aside>
💡 **Jupyter Notebook 시작 폴더 위치 바꾸기**

</aside>

1. prompt에서 jupyter notebook --generate-config
2. 생성한 jupyter_notebook_config.py 찾아서 메모장으로 열기. 일반적인 경우에는 C:\Users\username\.jupyter\jupyter_notebook_config.py에 위치해 있다.

![꿀팁… 그냥 파일탐색기에서 c드라이브로 이동해서 ju만 쳐도 뜬다!](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%202.png)

꿀팁… 그냥 파일탐색기에서 c드라이브로 이동해서 ju만 쳐도 뜬다!

1. ctrl + F 하고 c.NotebookApp.notebook_dir = '’  찾아주고 뒤에 원하는 시작위치로 변경해준다. (내 경우에는 c.NotebookApp.notebook_dir = ‘F:/’)

*주의할 점은 앞에 주석처리를 위해 # 처리가 되어 있는데 이 것을 지워주어야 바꾼 configuration이 저장이 된다.

완료하면 다음과 같이 원하는대로 바뀐 시작 폴더를 확인할 수 있다.

![시작 폴더 변경 이후 jupyter notebook 초기 화면](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%203.png)

시작 폴더 변경 이후 jupyter notebook 초기 화면

<aside>
💡 **Jupyter lab 시작 폴더 위치 바꾸기**

</aside>

노트북과 99% 비슷하지만 구글에서 정보와 **다른 부분**이 있으니 눈을 조금만 크게 뜨고 보기 바란다. 차근차근 정리하면, 

1. prompt에서 jupyter **lab** --generate-config
2. 생성한 jupyter_lab_config.py 찾아서 메모장으로 열기. 
3. ctrl + F 하고 **c.ServerApp.notebook_dir = '’**  찾으면 해당 명령어(?)가 DEPRECATED 되었다는 안내가 뜬다. 
    
    ![Untitled](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%204.png)
    
4. notebook_dir 대신 → root_dir 명령어를 이용한다. (내 경우에는 c.ServerApp.root_dir = 'F:/’)

마찬가지로 주피터 랩에서도 완료. 😃

![시작 폴더 변경 이후 jupyter lab 초기 화면](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%205.png)

시작 폴더 변경 이후 jupyter lab 초기 화면

~~별 것도 아닌데, 1시간이나 잡아 먹었다. 주석처리(#) 안 지워서 20분, 구글에서 알려준 c.ServerApp.notebook_dir 가 deprecated되었다는 걸 못 봐서 20분, ‘F:/’ 를 ‘:F/’로 잘못 적어서 20분… 😒~~

다른 분들이 이런 사소한(?) 일로 불편을 겪지 않았으면 좋겠다!

나름 거의(?) 첫 포스트라고 보여줬더니 반응…ㅋㅋㅋ

![Untitled](JupyterNotebook,%20Jupyter%20lab%20%E1%84%89%E1%85%B5%E1%84%8C%E1%85%A1%E1%86%A8%20%E1%84%91%E1%85%A9%E1%86%AF%E1%84%83%E1%85%A5%20%E1%84%8B%E1%85%B1%E1%84%8E%E1%85%B5%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%2005429dd949f943cd955b0c98ea1f1a4f/Untitled%206.png)

🙂😊😂😎👹 이모티콘 백만개로 다시 마무리한다!!!

---

> (2022.10.15) 시작 폴더 변경한 직후, pandas, numpy가 import되지 않는 일이 발생했는데 내 경우에는 콘다를 몇 번 껐다 키니 원래대로 작동했다. 무슨 문제인 지는 모르겠다.
>