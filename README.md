## π©π»βπΌ Ms.TROMM

### Wise Secretary Always Thinking about You:

### Artificial Intelligence-based Recommendation Software using Stylers and Smart Mirror

---

## π₯ Contributors

##### JIN HO KIM, Department of Information System

##### GA HEE HAN, Chinese Language and Literature

##### YU JIN HER, Department of Information System

##### EO JIN LEE, Department of Information System

---

## β¨ Details

[Link to Notion](https://dot-nasturtium-ee3.notion.site/Ms-TROMM-e65d5d40ac7044b797a5c9955d5e4b8d)

---

## π Methodolgy

> ### **Stacks :** Flutter(frontend),Python flask(backend), MySQL(DB), etc

</br>

## 1. Flutter(frontend)

`dir > Ms-TROMM/MsTROMM_Frontend/lib/ui`

- μλλ‘μ΄λμ iOS νκ²½μμ λͺ¨λ κ°λ°μ΄ κ°λ₯νκ³  κ΅¬κΈμμ DartμΈμ΄λ₯Ό κΈ°λ°μΌλ‘ μ μν μΉ/μ± ν¬λ‘μ€νλ«νΌ νλ μμν¬μΈ Flutter μ¬μ©
- λ°±μ€λ μμ²΄ νΉμ λ°μ΄ν°λ² μ΄μ€λ‘λΆν° κ°κ³΅ν json νμμ λ°μ΄ν°λ₯Ό λ°±μ€λλ‘λΆν° μμ²­νμ¬ Ms.TROMM μ¬μ©μλ€μ΄ μ¬μ©νκΈ° μ½λλ‘ λ³΄μ¬μ£Όλ μ­ν  μν
- μ¬μ©μλ‘λΆν° λ°μ μ λ³΄λ₯Ό λ°±μ€λ μλ²λ‘ μ λ¬νμ¬ λ°μ΄ν°λ² μ΄μ€μ μ μ₯(μλ°μ΄νΈ)νκ±°λ λ°±μ€λ μλ²κ° κ°κ³΅ν  μ μλλ‘ λ°μ΄ν°λ₯Ό μ κ³΅

* ν

  - λ μ¨λ₯Ό λ³΄μ¬μ£Όλ μμ ―
  - μ€νμΌλ¬ μλ μν νν μμ ―
  - μ€λ΄ μ μ΅, μλκ±΄μ‘° κΈ°λ₯ μ»¨νΈλ‘€λ¬ μμ ―
  - Bottom tab μ ν΅ν΄ μΆμ², μ€νμΌλ¬, μ€μ  ν­μΌλ‘ μ΄λ κ°λ₯
  - Firebase Cloud Messaging μ ν΅ν΄μ λ°μμ¨ notification μ²λ¦¬ λ‘μ§ ν¬ν¨

  </br>

* μΆμ²

  - μ€λμ μΆμ²κ³Ό μ μ΄ μΆμ² ν­
  - λ΄ μ·μ₯μΌλ‘ μ΄λ κ°λ₯ν λ²νΌ μ‘΄μ¬

  </br>

* λ΄ μ·μ₯

  - λ΄ μ·μ₯μ λ±λ‘λ μ·λ€μ μλ²μμ μ½μ΄μ¨ ν λμ€νλ μ΄ ν¨
  - μ°μΈ‘ μλ¨μ μΉ΄λ©λΌ λ²νΌμ ν΄λ¦­ν΄ λ΄ μ·μ λ±λ‘ν  μ μμ

    </br>

* μ€νμΌλ¬

  - μ€νμΌλ¬λ₯Ό κ°λ¨ν μ μ΄ν  μ μλ UI μ κ³΅
  - μ€νμΌλ§ μ½μ€λ₯Ό μ νν  μ μλ UI μ κ³΅
  - μ€νμΌλ¬ λ° μ€λ§νΈ λ―Έλ¬μ μ°κ²° μνμ λν νν©ν μ κ³΅

    </br>

* μ€μ 

  - μ¬μ©μ μ λ³΄ λ³κ²½ κ°λ₯
  - νΈμμλ¦Ό μ€μ 
  - μ½κ΄ λ° λ²μ  μ λ³΄
  - λ‘κ·Έμμ κΈ°λ₯

  </br>

* κΈ°ν
  - νν λ¦¬μΌ νλ©΄ (lib/ui/authentication/tutorial.dart)
    - μ± μ¬μ© λ°©μμ λν κ°λ¨ν ν¬ν λ¦¬μΌ νμ΄μ§ μ κ³΅
  - λ‘κ·ΈμΈ νλ©΄ (lib/ui/authentication/login.dart)
    - μ¬μ©μ μ΄λ©μΌ, λΉλ°λ²νΈ μλ ₯ ν λ‘κ·ΈμΈ κ°λ₯
  - νμκ°μ νλ©΄ (lib/ui/authentication/signup.dart)
    - μ¬μ©μ μ΄λ©μΌ, λΉλ°λ²νΈ, μ±λ³, μΆμλλ μλ ₯ ν νμκ°μ κ°λ₯
    - νμκ°μ μ μ€λ¬Έμ ν΅ν΄ μ¬μ©μμ μ νΈ λ±λ‘ κ°λ₯ (lib/ui/survey)
    - μ€λ¬Έ λ΄μ©μ μ¬μ©μμ μ νΈ μμ, μ νΈ ν₯, μ νΈ μλ₯ μ νμΌλ‘ κ΅¬μ±λ¨

</br>

`Firebase Cloud Messaging`

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

</br>

`API service`

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

- **μ¬μ©μ(frontend)μκ² μ λ¬λ°μ μ λ³΄(json)λ₯Ό ν΅ν΄ μ¬μ©μκ° μνλ μ λ³΄λ₯Ό, μνλ λ°©μμΌλ‘ λ³Ό μ μλλ‘ frontendμκ² λ€μ μ λ¬νλ Part(by Restful API)**
- μ¬μ©μκ° μνλ μ λ³΄λ₯Ό DBλ‘λΆν° κ°μ Έμμ κ°κ³΅νμ¬ frontendκ° μ¬μ©μμκ² μνλ λ°©μμΌλ‘ μ λ¬ν  μ μλλ‘ νλ Part(by Restful API)

```python
# restful API ex.
@app.route('/alerts/<userid>',methods = ['GET'])
@swag_from(specs_dict)
def alert(userid):
    # "μ€λμ μΆμ²" μλ¦Ό (/recommend/today/<city>/<userid> μ κ΅¬ν)
    # "μ μ΄ μΆμ²" μλ¦Ό (/recommands/control/<userid> μ κ΅¬ν)
    # "μ€νμΌλ¬ μν" μλ¦Ό(μ€νμΌλ¬ κ°λ) (/state/stylers/<userid> μ κ΅¬ν)
    # "μ€νμΌλ¬ μν" μλ¦Ό(λ¬Όμν) (/styler/water/<userid>μ κ΅¬ν)
    # "μΌμ " μλ¦Ό (/schedule/<userid> μ κ΅¬ν)

    push = User.query.filter(User.id==userid).first().push
    if push == 0:
        return jsonify("Ms.TROMMμ λ§μΆ€ν μΆμ² λ΄μ­μ λ³΄μλ €λ©΄ νΈμ μλμ μΌμ£ΌμμΌ ν©λλ€!")

    values = StylerAlert.query.filter(StylerAlert.user_id==userid).all()
    dict_li =[]
    for i in range(0,len(values)):
        dict_li.append({"title":values[i].title, "description":values[i].description,"created_at":values[i].created_at})
    if len(dict_li)==0:
        return jsonify("μλ¦Ό λ΄μ­μ΄ μμ΅λλ€! κ³§ μ’μ μΆμ² μλ €λλ¦΄κ²μ!")
    else:
        return jsonify(dict_li)
```

- νλ‘μ νΈ λ°μ΄ν° λͺ¨λΈμ μ μ§ κ΄λ¦¬ λ° λ³΄μμ μ©μ΄μ±μ μν΄ SqlAlchemyλ₯Ό ν΅ν΄ ORM(Object-Relationship-Model)μ κ΅¬ν

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

- μΆκ°μ μΌλ‘ SqlAlchemyμ queryμ κ°μ DB λͺ¨λΈλ§μ ν΅ν΄ μ»μ dataλ€μ responseκ°(json)μΌλ‘ μ½κ² schemingνμ¬ request μμ²­ν client Serverμκ² λμ Έμ£ΌκΈ° μν΄ marshmallowλ₯Ό νμ©

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

- νλ‘ νΈμ€λμ Restful API μν΅μ μν΄ Swagger μ¬μ©

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

- μ€νμΌλ¬μ NeedStyler value Updateλ₯Ό μν΄ νμ΅λͺ¨λΈ μ¬μ©

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

```python
def need_styler(clothes,userid):
    cal = calendar()
    cal = json.loads(cal)
    cal_li = cal['items'][0:]
    sch_li = [] # μΌμ  λ¦¬μ€νΈ
    sch_date = [] # μΌμ μ λν date λ¦¬μ€νΈ

    ## λ¦¬μ€νΈμ μμ μΆκ°
    for i in range(0,len(cal_li)):
        sch_li.append(cal_li[i]['summary'])
        sch_date.append(cal_li[i]['start'])

    # μΌμ μ λν dict λ§λ€κΈ°
    sch_dict = dict(zip(sch_li,sch_date))

    new_clothes = Clothes.query.filter(Clothes.name ==clothes).first()
    schema = clotheSchema()
    clo_json = schema.dump(new_clothes)
    last_time = datetime.date.today() - datetime.date(int(clo_json['stylered_at'][0:4]),int(clo_json['stylered_at'][5:7]),int(clo_json['stylered_at'][8:10])) # λ§μ§λ§ μ€νμΌλ¬ κ°λμΌλ‘λΆν° μ§λ μκ°


    #### μΆμ² μκ³ λ¦¬μ¦(μΌμ  & λ§μ§λ§ μ€νμΌλ¬ κ°λλ μ§λ₯Ό κ³ λ €ν)
    timedel = np.timedelta64(last_time,'ns')
    day = timedel.astype('timedelta64[D]')
    day = day.astype(int)

    # λ°μ΄ν° μμ ν΅ν΄ νμ΅
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
                testing = 1 # μΊλ¦°λμ μμ²­ν μ·μ κ΄ν μ€μΌμ₯΄μ΄ μ‘΄μ¬
                break
            else :
                testing = 0 # μΊλ¦°λμ μμ²­ν μ·μ κ΄ν μ€μΌμ₯΄ X

        if testing == 1:
            tm = 2*day + np.exp2(6-new_day) # κΈ°μ€ ν¨μ
            ### need_styler_set : 0 = λ§€μ°νμ 1 = νμ 2 = κ΄μ°?μ
            if tm >= 8:
                need_styler_set = 0 # λ§€μ° νμ

            elif tm >= 6 and tm < 8:
                need_styler_set = 1 # νμ

            else :
                need_styler_set = 2 # κ΄μ°?μ

        elif testing == 0:
            tm = 2*day + np.exp2(6-new_day) # κΈ°μ€ ν¨μ
            if tm >= 8:
                need_styler_set = 0 # λ§€μ° νμ

            elif tm >= 6 and tm < 8:
                need_styler_set = 1 # νμ

            else :
                need_styler_set = 2 # κ΄μ°?μ


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
### datasetμ νμ΅νλ κ³Όμ 
def control_csv(clothe, userid):
    data = pd.read_csv('flaskr/dataset.csv')
    data = pd.DataFrame(data)
    cal = calendar()
    cal = json.loads(cal)
    cal_li = cal['items'][0:]
    sch_li = [] # μΌμ  λ¦¬μ€νΈ
    sch_date = [] # μΌμ μ λν date λ¦¬μ€νΈ
    match_li = []
    to_update = []

    ## λ¦¬μ€νΈμ μμ μΆκ°
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
    ### DB λΉμ΄μλμ§ νμΈ
    if type(new_sch_count) == type(None):
        for i in range(0, len(to_update)):
            new_schdule = Schedule(id = i+1, cont = i+1, user_id=userid, title=to_update[i], description=to_update[i]).create()
    return match_li
```

```python
### DBμ μ μ λ₯Ό ν΅ν΄ νμ΅νλ func
specs_dict = AddCSV().specs_dict
@app.route('/clothe/schedule/<userid>', methods = ['POST'])
@swag_from(specs_dict)
def add_csv(userid):
    data = request.get_json()

    '''
    ex.
    {
        "LGμ μλ©΄μ " : "μ μ₯",
        "λ‘―λ°μλ" : "ν°μμΈ "
    }
    '''

    dataFrame = pd.read_csv('flaskr/dataset.csv')
    dataFrame = pd.DataFrame(dataFrame)
    data_dict = dataFrame.to_dict()


    ### νμ΅ λ°μ΄ν° μ(csv) μλ°μ΄νΈλ₯Ό μν λμλλ¦¬
    for i in range(len(data)):
        target_num = max(list(data_dict[list(data.values())[i]].keys()))+1
        target = list(data.keys())[i]
        data_dict[list(data.values())[i]].update({target_num:target})

    # Dict -> CSV
    new_df = pd.DataFrame(data_dict)
    new_df.to_csv('flaskr/dataset.csv')


    # νμ΅μ λλ λ°μ΄ν°λ DBμμ μ­μ 
    Schedule.query.filter(Schedule.user_id == userid).delete()
    db.session.commit()
    return 'finish update!'
```

- API(openWeatherMap, GoogleCal)λ₯Ό νμ©νμ¬ μΆμ²μμ€ν κ΅¬μΆ

```python
# λ μ¨ api κ°μ Έμ€κΈ°
def getWeather(city):
    openweather_api_url = "https://api.openweathermap.org/data/2.5/"
    ### envνμΌμ ν΅ν΄ api key hide
    service_key = environ.get('weatherApiKey')

    # API μμ²­μ νμν μΈμκ° μ μ
    ow_api_url = openweather_api_url + "weather"
    payload = "?q=" + str(city) + "&" + "appid=" + service_key + "&lang=kr"
    url_total = ow_api_url + payload

    # API μμ²­νμ¬ λ°μ΄ν° λ°κΈ°
    req = urllib.request.urlopen(url_total)
    res = req.readline()
    # λ°μ κ° JSON ννλ‘ μ μ νμ¬ λ°ν
    items = json.loads(res)
    return items
```

```python
## google calendar API
def calendar():
    api_url = "https://www.googleapis.com/calendar/v3/calendars/{calID}/events?orderBy=startTime&singleEvents=true&timeMax="
    # using .env
    service_key = environ.get('googleapi')

    # API μμ²­μ νμν μΈμκ° μ μ
    ## κΈ°μ€μκ° μ λ€ 100μΌκ°μ λ°μ΄ν° μμ§
    time_min = (datetime.date.today() + datetime.timedelta(days=-100)).isoformat() + "T00:00:00Z"
    time_max = (datetime.date.today() + datetime.timedelta(days=100)).isoformat() + "T23:59:59Z"
    url_total = api_url + time_max + "&timeMin=" + time_min + "&key=" + service_key

    # API μμ²­νμ¬ λ°μ΄ν° λ°μμ jsonμΌλ‘ return
    req = requests.get(url_total)
    items = req.json()
    return json.dumps(items, ensure_ascii=False)
```

  <br />

## 3. MySQL+Heroku(DB)

- **μ€μκ°μΌλ‘ μ λ³΄λ₯Ό κ΅ννκ³  μλ°μ΄νΈ λ° νμ΅κ³Όμ μ κ±°μΉλ Part**

- κΈ°μ‘΄μ κ΅¬μΆν΄λ SqlAlchemyμ ORM modelsλ₯Ό ν΅ν΄ νμ΄μ¬ μ½λλ‘ SQL Ccontrol

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/main.py`

  `dir > Ms-TROMM/MsTROMM_Backend/flaskr/models`

```python
 # ex. Schedule Model
from ..main import db
from marshmallow import Schema, fields

class Schedule(db.Model):
    ## table μμ± by SqlAlchemy
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

- MySQLμ μ¬μ©νμ¬ μκ²©μΌλ‘ λ°μ΄ν°λ² μ΄μ€λ₯Ό κ΄λ¦¬
- μΌμ  νΈλν½μ MySQLμ λ¬΄λ£λ‘ νΈμ€ν ν  μ μλλ‘ ν΄μ£Όλ μλ²μΈ Heroku μλΉμ€μ MySQLμ μ°κ²°νμ¬, μ€μκ°μΌλ‘ λ°μ΄ν°λ² μ΄μ€μ λ°μ΄ν°λ₯Ό μ½κ³  μλ°μ΄νΈν  μ μλλ‘ νμ©

    <img width="343" alt="heroku" src="https://user-images.githubusercontent.com/50936176/145680199-fa7b7373-b2b6-4265-910b-e66fc0188258.png">

</br>

- MySQLμ Heroku μλ²μ clearDBμ μ°κ²°νμ¬, μ΄λ₯Ό JetBrainμ Datagripμ ν΅ν΄ λ°μ΄ν°κ° μ λλ‘ μλ°μ΄νΈ λμλμ§λ₯Ό μ€μκ°μΌλ‘ νμΈ
  </br>
  <img width="853" alt="db" src="https://user-images.githubusercontent.com/50936176/145680197-4dea4f8e-5cf9-404c-be4f-9c7ba2d739cd.png">

</br>

- Herokuλ₯Ό ν΅ν΄ νλ‘ νΈμ€λμ λ°±μ€λ(λ°μ΄ν°λ² μ΄μ€) κ°μ λ°μ΄ν°λ₯Ό μ£Όκ³ λ°λ μνν μ€μκ° μν΅ κ΅¬ν

  `dir > Ms-TROMM/MsTROMM_Backend/Procfile`

  [Link of Heroku Server](https://ms-tromm.herokuapp.com/)

- dbdiagram.io μ¬μ΄νΈλ₯Ό νμ©νμ¬ SQLκ³Ό μ μ¬ν μ½λ(νμ΄λΈ, μΈλ±μ€ λ±)λ₯Ό μ½μνλ©΄ μλμΌλ‘ ERDλ₯Ό μμ±

     <img width="954" alt="dbdiagram io" src="https://user-images.githubusercontent.com/92378089/145702603-e33531e4-3468-4dc5-a3e8-873ad02ad508.PNG">
