## 🖥️ Ms.TROMM

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

[Link to Notion](https://dot-nasturtium-ee3.notion.site/Ms-TROMM-60cbd1c9759f438e8e7ede45385a6d1b)

---

## 🖥️ Methodolgy

> ### **Stacks :** Flutter(frontend),Python flask(backend), MySQL(DB), etc

## 1. Flutter(frontend)

-

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

-
