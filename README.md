## 👩🏻‍💼 Ms.TROMM

### Wise Secretary Always Thinking about You:

### Artificial Intelligence-based Recommendation Software using Stylers and Smart Mirror

---

## 🔥 Contributors

##### JIN HO KIM, Department of Information System

##### GA HEE HAN, Chinese Language and Literature

##### YU JIN HER, Department of Information System

##### EO JIN LEE, Department of Information System

---

## ✨ Details

[Link to Notion](https://dot-nasturtium-ee3.notion.site/Ms-TROMM-e65d5d40ac7044b797a5c9955d5e4b8d)

---

## 🔋 Methodolgy

> ### **Stacks :** Flutter(frontend),Python flask(backend), MySQL(DB), etc

</br>

## 1. Flutter(frontend)

- 안드로이드와 iOS 환경에서 모두 개발이 가능하고 구글에서 Dart언어를 기반으로 제작한 웹/앱 크로스플랫폼 프레임워크인 Flutter 사용
- 백앤드 자체 혹은 데이터베이스로부터 가공한 json 타입의 데이터를 백앤드로부터 요청하여 Ms.TROMM 사용자들이 사용하기 쉽도록 보여주는 역할 수행
- 사용자로부터 받은 정보를 백앤드 서버로 전달하여 데이터베이스에 저장(업데이트)하거나 백앤드 서버가 가공할 수 있도록 데이터를 제공

### 화면

* Home (lib/ui/home)
  * 날씨를 보여주는 위젯 
  * 스타일러 작동 상태 표현 위젯 
  * 실내 제습, 자동건조 기능 컨트롤러 위젯 
  * Bottom tab 을 통해 추천, 스타일러, 설정 탭으로 이동 가능 
  * Firebase Cloud Messaging 을 통해서 받아온 notification 처리 로직 포함 

* 추천 (lib/ui/recommendation)
  * 오늘의 추천과 제어 추천 탭 
  * 내 옷장으로 이동 가능한 버튼 존재 

* 내 옷장 (lib/ui/recommendation/my_closet.dart)
  * 내 옷장에 등록된 옷들을 서버에서 읽어온 후 디스플레이 함 
  * 우측 상단의 카메라 버튼을 클릭해 내 옷을 등록할 수 있음 
  
* 스타일러 (lib/ui/styler)
  * 스타일러를 간단히 제어할 수 있는 UI 제공 
  * 스타일링 코스를 선택할 수 있는 UI 제공 
  * 스타일러 및 스마트 미러의 연결 상태에 대한 현황판 제공 

* 설정 (lib/ui/settings)
  * 사용자 정보 변경 가능 
  * 푸시알림 설정 
  * 약관 및 버전 정보 
  * 로그아웃 기능 

* 기타 
  * 투토리얼 화면 (lib/ui/authentication/tutorial.dart)
    * 앱 사용 방식에 대한 간단한 투토리얼 페이지 제공
  * 로그인 화면 (lib/ui/authentication/login.dart)
    * 사용자 이메일, 비밀번호 입력 후 로그인 가능 
  * 회원가입 화면 (lib/ui/authentication/signup.dart) 
    * 사용자 이메일, 비밀번호, 성별, 출생년도 입력 후 회원가입 가능 
    * 회원가입 시 설문을 통해 사용자의 선호 등록 가능 (lib/ui/survey)
      * 설문 내용은 사용자의 선호 색상, 선호 향, 선호 의류 유형으로 구성됨 

### 주요 로직 

#### Firebase Cloud Messaging 처리 

```dart 

class _HomePageState extends State<HomePage> {
  late FirebaseMessaging messaging;
    ... 

  @override
  void initState() {
    super.initState();

    messaging = FirebaseMessaging.instance;
    messaging.getToken().then((value) {
      print(value);
    });

    FirebaseMessaging.onMessage.listen((RemoteMessage event) {
      print("message recieved");
      print(event.notification!.body);
      if (event.notification!.title == 'feedback') {
     
     ...
    }

```

#### API service

```dart 
ApiService apiService = ApiService();

class ApiService {
  static const url = "https://ms-tromm.herokuapp.com/";

// endpoint 
  static const getAllUserClothes = "users/clothes/";

  Future<List<UserClothes>> fetchUserClothes(int userId) async {
    final response =
        await http.get(Uri.parse(url + getAllUserClothes + userId.toString()));
    List<UserClothes> listOfUserClothes = [];

    if (response.statusCode == 200) {
      List<dynamic> list = <dynamic>[];
      list = json.decode(response.body);
      print(list);
      if (list.isNotEmpty) {
        for (int i = 0; i < list.length; i++) {
          if (list[i] != null) {
            Map<String, dynamic> map = list[i];
            listOfUserClothes.add(UserClothes.fromJson(map));
          }
        }
      }
      return Future.value(listOfUserClothes);
    } else {
      throw Exception("API call failed");
    }
  }

```

<br />

## 2. Flask(backend)

`dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

- **사용자(frontend)에게 전달받은 정보(json)를 통해 사용자가 원하는 정보를, 원하는 방식으로 볼 수 있도록 frontend에게 다시 전달하는 Part(by Restful API)**
- 사용자가 원하는 정보를 DB로부터 가져와서 가공하여 frontend가 사용자에게 원하는 방식으로 전달할 수 있도록 하는 Part(by Restful API)

```python
# restful API ex.
@app.route('/alerts/<userid>',methods = ['GET'])
@swag_from(specs_dict)
def alert(userid):
    # "오늘의 추천" 알림 (/recommend/today/<city>/<userid> 에 구현)
    # "제어 추천" 알림 (/recommands/control/<userid> 에 구현)
    # "스타일러 상태" 알림(스타일러 가동) (/state/stylers/<userid> 에 구현)
    # "스타일러 상태" 알림(물상태) (/styler/water/<userid>에 구현)
    # "일정" 알림 (/schedule/<userid> 에 구현)

    push = User.query.filter(User.id==userid).first().push
    if push == 0:
        return jsonify("Ms.TROMM의 맞춤형 추천 내역을 보시려면 푸시 알람을 켜주셔야 합니다!")

    values = StylerAlert.query.filter(StylerAlert.user_id==userid).all()
    dict_li =[]
    for i in range(0,len(values)):
        dict_li.append({"title":values[i].title, "description":values[i].description,"created_at":values[i].created_at})
    if len(dict_li)==0:
        return jsonify("알림 내역이 없습니다! 곧 좋은 추천 알려드릴게요!")
    else:
        return jsonify(dict_li)
```

- 프로젝트 데이터 모델의 유지 관리 및 보수의 용이성을 위해 SqlAlchemy를 통해 ORM(Object-Relationship-Model)을 구현

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/models`

```python
from flask_sqlalchemy import SQLAlchemy
db = SQLAlchemy(app)

### data models(tables)
from flaskr.models.user import User, UserSchema
from flaskr.models.clothes import Clothes, clotheSchema
from flaskr.models.scent import Scent
from flaskr.models.clothes_combination import ClothesCombination
from flaskr.models.control import Control, controlSchema
from flaskr.models.recommendation import Recommendation
from flaskr.models.schedule import Schedule
from flaskr.models.styler_alert import StylerAlert, alertSchema
from flaskr.models.user_preference import UserPreference, preferSchema
from flaskr.models.styler import Styler, stylerSchema
from flaskr.models.mirror import Mirror,MirrorSchema
db.create_all()
```

- 추가적으로 SqlAlchemy의 query와 같은 DB 모델링을 통해 얻은 data들을 response값(json)으로 쉽게 scheming하여 request 요청한 client Server에게 던져주기 위해 marshmallow를 활용

```python
from flask_marshmallow import Marshmallow
from marshmallow import Schema, fields, pprint
ma = Marshmallow(app)

### ex. WeatherSchema
class weatherSchema(Schema):
    high_temp = fields.Integer()
    low_temp = fields.Integer()
    daily = fields.Integer()
```

- 프론트앤드와 Restful API 소통을 위해 Swagger 사용

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/Swg.py`

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

```python
swagger = Swagger(app)

# ex
specs_dict = Status().specs_dict
@swag_from(specs_dict)
```

<img width="1374" alt="apidocs" src="https://user-images.githubusercontent.com/50936176/145680194-6a1c7047-91b6-420e-94ab-56b6cd072516.png">

</br>

- 스타일러의 NeedStyler value Update를 위해 학습모델 사용

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

```python
def need_styler(clothes,userid):
    cal = calendar()
    cal = json.loads(cal)
    cal_li = cal['items'][0:]
    sch_li = [] # 일정 리스트
    sch_date = [] # 일정에 대한 date 리스트

    ## 리스트에 요소 추가
    for i in range(0,len(cal_li)):
        sch_li.append(cal_li[i]['summary'])
        sch_date.append(cal_li[i]['start'])

    # 일정에 대한 dict 만들기
    sch_dict = dict(zip(sch_li,sch_date))

    new_clothes = Clothes.query.filter(Clothes.name ==clothes).first()
    schema = clotheSchema()
    clo_json = schema.dump(new_clothes)
    last_time = datetime.date.today() - datetime.date(int(clo_json['stylered_at'][0:4]),int(clo_json['stylered_at'][5:7]),int(clo_json['stylered_at'][8:10])) # 마지막 스타일러 가동으로부터 지난 시간


    #### 추천 알고리즘(일정 & 마지막 스타일러 가동날짜를 고려한)
    timedel = np.timedelta64(last_time,'ns')
    day = timedel.astype('timedelta64[D]')
    day = day.astype(int)

    # 데이터 셋을 통해 학습
    standard = control_csv(clothes,userid)
    print(type(standard))
    if len(standard) != 0:
        event_date = sch_dict[standard[0]]['date']
        new_timedel =  datetime.date(int(event_date[0:4]),int(event_date[5:7]),int(event_date[8:10])) - datetime.date.today()
        new_timedel = np.timedelta64(new_timedel,'ns')
        new_day = new_timedel.astype('timedelta64[D]')
        new_day = new_day.astype(int)
        df = pd.read_csv('flaskr/dataset.csv')
        df = pd.DataFrame(df)
        for i in range(0,min(len(df[clothes].tolist()),len(sch_li))):
            if (sch_li[i] in df[clothes].tolist()) == True :
                testing = 1 # 캘린더에 요청한 옷에 관한 스케쥴이 존재
                break
            else :
                testing = 0 # 캘린더에 요청한 옷에 관한 스케쥴 X

        if testing == 1:
            tm = 2*day + np.exp2(6-new_day) # 기준 함수
            ### need_styler_set : 0 = 매우필요 1 = 필요 2 = 괜찮음
            if tm >= 8:
                need_styler_set = 0 # 매우 필요

            elif tm >= 6 and tm < 8:
                need_styler_set = 1 # 필요

            else :
                need_styler_set = 2 # 괜찮음

        elif testing == 0:
            tm = 2*day + np.exp2(6-new_day) # 기준 함수
            if tm >= 8:
                need_styler_set = 0 # 매우 필요

            elif tm >= 6 and tm < 8:
                need_styler_set = 1 # 필요

            else :
                need_styler_set = 2 # 괜찮음


        # need_styler update
        new_clothes.need_styler = need_styler_set
        db.session.commit()
        result = schema.dump(new_clothes)
        return result
    else:
        result = schema.dump(new_clothes)
        return result
```

```python
### dataset을 학습하는 과정
def control_csv(clothe, userid):
    data = pd.read_csv('flaskr/dataset.csv')
    data = pd.DataFrame(data)
    cal = calendar()
    cal = json.loads(cal)
    cal_li = cal['items'][0:]
    sch_li = [] # 일정 리스트
    sch_date = [] # 일정에 대한 date 리스트
    match_li = []
    to_update = []

    ## 리스트에 요소 추가
    for i in range(0,len(cal_li)):
        sch_li.append(cal_li[i]['summary'])
        sch_date.append(cal_li[i]['start'])

    dataf = data[clothe].dropna(how='any').tolist()
    new_sch_li = [i.replace(' ',' ') for i in sch_li]
    for i in range(0,min(len(dataf),len(new_sch_li))):
        if (new_sch_li[i] in dataf) == True:
            match_li.append(new_sch_li[i])
        else:
            to_update.append(new_sch_li[i])

    new_sch_count = Schedule.query.filter_by(user_id=userid).first()
    ### DB 비어있는지 확인
    if type(new_sch_count) == type(None):
        for i in range(0, len(to_update)):
            new_schdule = Schedule(id = i+1, cont = i+1, user_id=userid, title=to_update[i], description=to_update[i]).create()
    return match_li
```

```python
### DB와 유저를 통해 학습하는 func
specs_dict = AddCSV().specs_dict
@app.route('/clothe/schedule/<userid>', methods = ['POST'])
@swag_from(specs_dict)
def add_csv(userid):
    data = request.get_json()

    '''
    ex.
    {
        "LG전자면접" : "정장",
        "롯데월드" : "티셔츠"
    }
    '''

    dataFrame = pd.read_csv('flaskr/dataset.csv')
    dataFrame = pd.DataFrame(dataFrame)
    data_dict = dataFrame.to_dict()


    ### 학습 데이터 셋(csv) 업데이트를 위한 딕셔너리
    for i in range(len(data)):
        target_num = max(list(data_dict[list(data.values())[i]].keys()))+1
        target = list(data.keys())[i]
        data_dict[list(data.values())[i]].update({target_num:target})

    # Dict -> CSV
    new_df = pd.DataFrame(data_dict)
    new_df.to_csv('flaskr/dataset.csv')


    # 학습을 끝난 데이터는 DB에서 삭제
    Schedule.query.filter(Schedule.user_id == userid).delete()
    db.session.commit()
    return 'finish update!'
```

- API(openWeatherMap, GoogleCal)를 활용하여 추천시스템 구축

```python
# 날씨 api 가져오기
def getWeather(city):
    openweather_api_url = "https://api.openweathermap.org/data/2.5/"
    ### env파일을 통해 api key hide
    service_key = environ.get('weatherApiKey')

    # API 요청시 필요한 인수값 정의
    ow_api_url = openweather_api_url + "weather"
    payload = "?q=" + str(city) + "&" + "appid=" + service_key + "&lang=kr"
    url_total = ow_api_url + payload

    # API 요청하여 데이터 받기
    req = urllib.request.urlopen(url_total)
    res = req.readline()
    # 받은 값 JSON 형태로 정제하여 반환
    items = json.loads(res)
    return items
```

```python
## google calendar API
def calendar():
    api_url = "https://www.googleapis.com/calendar/v3/calendars/{calID}/events?orderBy=startTime&singleEvents=true&timeMax="
    # using .env
    service_key = environ.get('googleapi')

    # API 요청시 필요한 인수값 정의
    ## 기준시간 앞 뒤 100일간의 데이터 수집
    time_min = (datetime.date.today() + datetime.timedelta(days=-100)).isoformat() + "T00:00:00Z"
    time_max = (datetime.date.today() + datetime.timedelta(days=100)).isoformat() + "T23:59:59Z"
    url_total = api_url + time_max + "&timeMin=" + time_min + "&key=" + service_key

    # API 요청하여 데이터 받아서 json으로 return
    req = requests.get(url_total)
    items = req.json()
    return json.dumps(items, ensure_ascii=False)
```

  <br />

## 3. MySQL+Heroku(DB)

- **실시간으로 정보를 교환하고 업데이트 및 학습과정을 거치는 Part**

- 기존에 구축해둔 SqlAlchemy의 ORM models를 통해 파이썬 코드로 SQL Ccontrol

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/models`

```python
 # ex. Schedule Model
from ..main import db
from marshmallow import Schema, fields

class Schedule(db.Model):
    ## table 생성 by SqlAlchemy
    __tablename__ = 'schedule'

    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    user_id = db.Column(db.Integer, db.ForeignKey('user.id'), nullable=False)
    title = db.Column(db.String(100))
    description = db.Column(db.String(255))
    cont = db.Column(db.Integer)
    datetime = db.Column(db.DateTime, nullable=False, server_default=db.func.now())

    # init
    def __init__(self,id, user_id, title, description, cont):
        self.id = id
        self.cont = cont
        self.description = description
        self.user_id = user_id
        self.title = title

    # db add and commit
    def create(self):
        db.session.add(self)
        db.session.commit()
        return self
```

- MySQL을 사용하여 원격으로 데이터베이스를 관리
- 일정 트래픽의 MySQL을 무료로 호스팅 할 수 있도록 해주는 서버인 Heroku 서비스와 MySQL을 연결하여, 실시간으로 데이터베이스의 데이터를 읽고 업데이트할 수 있도록 활용

    <img width="343" alt="heroku" src="https://user-images.githubusercontent.com/50936176/145680199-fa7b7373-b2b6-4265-910b-e66fc0188258.png">

</br>

- MySQL을 Heroku 서버의 clearDB에 연결하여, 이를 JetBrain의 Datagrip을 통해 데이터가 제대로 업데이트 되었는지를 실시간으로 확인
  </br>
  <img width="853" alt="db" src="https://user-images.githubusercontent.com/50936176/145680197-4dea4f8e-5cf9-404c-be4f-9c7ba2d739cd.png">

</br>

- Heroku를 통해 프론트앤드와 백앤드(데이터베이스) 간의 데이터를 주고받는 원활한 실시간 소통 구현

  `dir > Ms-TROMM/MsTROMM_Backend/Procfile`

  [Link of Heroku Server](https://ms-tromm.herokuapp.com/)

- dbdiagram.io 사이트를 활용하여 SQL과 유사한 코드(테이블, 인덱스 등)를 삽입하면 자동으로 ERD를 생성

     <img width="954" alt="dbdiagram io" src="https://user-images.githubusercontent.com/92378089/145702603-e33531e4-3468-4dc5-a3e8-873ad02ad508.PNG">
