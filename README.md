# 1 - Crawling (크롤링)

* 아나콘다(https://www.anaconda.com/products/individual )’를 설치하여 파이썬과 라이브러리를 한번에 사용 할 수 있는 가상환경을 만들고 
주피터 노트북(https://jupyter.org/ )으로 실행
* Pandas 라이브러리를 통해 필요한 데이터만을 담은 data frame을 선언하고 이를 통해 머신러닝에 적용시킬 수 있음. 
인덱스가 있어 행과 열로 구성된 프레임에 데이터가 저장되는 테이블 형태의 data frame을 이용할 예정
* BeautifulSoup은 html 코드를 파이썬이 인식 할 수 있는 객체 구조로 변환하는 Parsing을 담당
* selenium은 브라우저 자동화도구로서 웹브라우저를 통해 동적페이지에서도 데이터 수집  가능

1) Anaconda Prompt

![1](https://user-images.githubusercontent.com/76679270/145396988-751b64cb-a10d-4afe-8854-5d2307d3e0b5.jpg)


2) 크롬드라이버 저장 경로 ,자신의 네이버 ID/PW입력

![2](https://user-images.githubusercontent.com/76679270/145397347-f68db065-170e-4a00-aed6-33135de8972b.jpg)
 

3) 데이터를 저장하려는 엑셀파일의 절대 경로를 입력

![3](https://user-images.githubusercontent.com/76679270/145397369-611f6349-8f61-4233-a045-7c063fada459.jpg)


4) 크롤링 되는 과정

![4](https://user-images.githubusercontent.com/76679270/145397412-f6a52c56-0aca-4205-9ad4-32f9f713dd5d.jpg)

  
5) 크롤링 완료 후 엑셀파일에 저장된 데이터 모습

![5](https://user-images.githubusercontent.com/76679270/145397428-777021fd-bb56-4170-b1de-4c3f4739c990.png)



# 2 - Preprocessing (전처리)
**크롤링한 데이터를 전처리하는 과정**

google colab에서 preprocessing.ipynb 파일을 열어 차례대로 실행한다.

1) 정제되지 않은 텍스트에 Py-Hanspell 적용
* Py-Hanspell은 네이버 맞춤법 검사기를 바탕으로 만들어진 한국어 전처리 패키지다. 
* 맞춤법 검사기를 import 하고 check를 하게 되면, 맞춤법과 띄어쓰기가 정확히 맞춰진다.

2) 문장 토큰화 도구 KSS 적용
* KSS는 한국어로 되어있는 텍스트를 문장 단위로 토큰화를 해주는 도구이다. 
* 위에서 맞춤법이 정확하게 맞춰진 텍스트에 KSS를 적용하면 문장 단위로 나누어지게 된다.

3) 형태소 분석 도구 KoNLPy 적용
* KoNLPy는 형태소 단위로 토큰화를 하는 도구이다. 
* KoNLPy를 통해서 사용할 수 있는 형태소 분석기에는 Okt(Open Korea Text), 메캅(Mecab), 코모란(Komoran), 한나눔(Hannanum), 꼬꼬마(Kkma)가 있다.
* 그중 Open Korea Text 를 사용하여 형태소 추출을 적용하게 되면 다음과 같이 토큰화 된다.


# 3 - LSTM


**LSTM으로 긍정적 vs 부정적 영화 리뷰 분류하기**

1. 코랩을 켜서 '파일'>'새 노트' 로 새 노트를 만들어주고 'LSTM_moviereview.py' 코드를 복사, 붙여넣기 해준다.

2. 데이터가 많아서 전처리와 학습, 정확도 도출 등이 오래걸릴 수 있다.


**LSTM으로 E vs I 분류하기**

   구글 스프레드 시트와 연동해서 데이터를 불러오는 방법을 사용했다.

1. mbti_train.xlsx와 mbti_test.xlsx를 다운받고, 구글 드라이브에 업로드해준다.

    (저자는 내 드라이브에 'mbti' 라는 폴더를 만들고 그 안에 
    
    mbti_train.xlsx 와 mbti_test.xlsx를 업로드해주었다.)


2. 코랩을 켜서 '파일'>'새 노트' 로 새 노트를 만들어주고 

    'mbti_LSTM.py' 코드를 복사, 붙여넣기 해준다.

3. 주석으로 "#훈련 데이터가 담긴 엑셀 파일의 구글 드라이브 경로" 라고 적힌 라인에는

    train 이라는 변수에 mbti_train.xlsx 파일의 구글 드라이브 경로를 적어준다.

4. 주석으로 "#테스트 데이터가 담긴 엑셀 파일의 구글 드라이브 경로" 라고 적힌 라인에는 

   test 라는 변수에 mbti_test.xlsx 파일의 구글 드라이브 경로를 저장해준다.

   예) 내 드라이브의 'mbti'라는 폴더에 저장해놓은 저자의 경우에는 
   
   train = '/content/drive/My Drive/mbti/mbti_train.xlsx'
   
   test = '/content/drive/My Drive/mbti/mbti_test.xlsx'
   
   라고 해주었다.

5. 그리고 '런타임'>'모두 실행' 하면, 
   '노트북에서 Google Drive 파일에 액세스하도록 허용하시겠습니까?' 라는 팝업창이 뜨는데, 

   'Google Drive에 연결'을 클릭해준다.

    그러면 '계정 선택' 창이 뜨는데, 계정을 선택해준 다음,
    
    '구글 계정에 액세스하려고 합니다.' 라는 창이 뜨면 '허용'을 눌러준다.

    (그리고 만약 콘솔창에 텍스트 필드가 뜬다면, 로그인 한 다음 암호가 뜰텐데, 
    
    그 암호를 복사해서 붙여넣기 해준다.)

    그러면 데이터 로드는 끝나고 다음 코드들이 진행된다.

# 4 - MLP
**1. 케라스의 texts_to_matrix() 이해하기**

구글 코랩을 켜서 '파일'>'새 노트' 로 새 노트를 만들어주고 
'1. 케라스의 texts_to_matrix() 이해하기' 코드를 전체 복사, 붙여넣기 해준 후
'런타임'>'모두 실행' 해준다.


**MLP로 E와 I 분류하기**

mbti_train.xlsx와 mbti_test.xlsx를 다운받고, 둘 다 구글 스프레드로 열어준 후 구글 드라이브에 저장해준다.

코랩을 켜서 '파일'>'새 노트' 로 새 노트를 만들어주고 
'2. 20개 뉴스 그룹(Twenty Newsgroups) 데이터에 대한 이해' 코드를 복사, 붙여넣기 해준다.

train 이라는 변수에 mbti_train.xlsx 파일의 구글 드라이브 경로를 적어주고
test 라는 변수에 mbti_test.xlsx 파일의 구글 드라이브 경로를 저장해준다.

'3. 다층 퍼셉트론(Multilayer Perceptron, MLP)을 사용하여 텍스트 분류하기' 코드도 복사, 붙여넣기 해준다.
'런타임'>'모두 실행' 하고, 구글에 로그인하게끔 하는 팝업창이 뜨는데, 그 팝업창을 통해 로그인을 한다.
(만약 팝업창에서 암호코드가 나오면 복사해서 콘솔창에 뜨는 필드에 붙여넣기 한다.)

데이터 양이 많기 때문에 훈련 데이터와 테스트 데이터를 모두 거쳐 전처리, 학습, 정확도 도출까지 시간이 걸릴 수 있다.
