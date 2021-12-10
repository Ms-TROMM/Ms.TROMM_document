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

## 1. Flutter(frontend)

- 안드로이드와 iOS 환경에서 모두 개발이 가능하고 구글에서 Dart언어를 기반으로 제작한 웹/앱 크로스플랫폼 프레임워크인 Flutter 사용
- 백앤드 자체 혹은 데이터베이스로부터 가공한 json 타입의 데이터를 백앤드로부터 요청하여 Ms.TROMM 사용자들이 사용하기 쉽도록 보여주는 역할 수행
- 사용자로부터 받은 정보를 백앤드 서버로 전달하여 데이터베이스에 저장(업데이트)하거나 백앤드 서버가 가공할 수 있도록 데이터를 제공


## 2. Flask(backend)

- 사용자(frontend)에게 전달받은 정보(json)를 통해 사용자가 원하는 정보를, 원하는 방식으로 볼 수 있도록 frontend에게 다시 전달하는 Part
- 사용자가 원하는 정보를 DB로부터 가져와서 가공하여 frontend가 사용자에게 원하는 방식으로 전달할 수 있도록 하는 Part
- 프로젝트 데이터 모델의 유지 관리 및 보수의 용이성을 위해 SqlAlchemy를 통해 ORM(Object-Relationship-Model)을 구현

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

## 3. MySQL(DB)

- 실시간으로 정보를 교환하고 업데이트 및 학습과정을 거치는 Part

- MySQL을 사용하여 원격으로 데이터베이스를 관리
- 기존에 구축해둔 sqlAlchemy의 ORM을 통해 파이썬 코드로 SQL을 조작

- 일정 트래픽의 MySQL을 무료로 호스팅 할 수 있도록 해주는 서버인 heroku 서비스와 MySQL을 연결하여, 실시간으로 데이터베이스의 데이터를 읽고 업데이트할 수 있도록 활용 
-  Heroku를 통해 프론트앤드와 백앤드(데이터베이스) 간의 데이터를 주고받는 원활한 실시간 소통 구현
- MySQL을 Heroku 서버의 clearDB에 연결하여, 이를 JetBrain의 Datagrip을 통해 데이터가 제대로 업데이트 되었는지를 실시간으로 확인
