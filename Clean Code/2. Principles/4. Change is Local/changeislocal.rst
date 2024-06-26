When a software system has to be maintained, extended and changed for a
long time, keeping change local reduces involved costs and risks. 

소프트웨어 시스탬이 장기간 유지보수되며, 확장및 변경 되어야 할때. 
변경을 국소화 하는 것은 관련 비용과 위험을 줄여준다.

Keeping change local means that there are boundaries in the design which changes
do not cross.

변경을 국소화 한다는 것은 설계에 경계가 있어 변경이 그 경계를 넘지 않는 다는 것을 의미하며,
이를 위해 낮은 결합도를 가진 소프트웨어가 필요 한 것이다.

높은 결합도(경계 없는 변경)
class DatabaseConnection:
    def query_user(self, user_id):
        # 데이터베이스에서 사용자 정보를 가져오는 로직
        return {"id": user_id, "name": "John Doe"}

class UserInterface:
    def __init__(self, db_connection):
        self.db_connection = db_connection

    def display_user(self, user_id):
        # DatabaseConnection을 직접 사용
        user = self.db_connection.query_user(user_id)
        print(f"User: {user}")

# 사용 예시
db_conn = DatabaseConnection()
ui = UserInterface(db_conn)
ui.display_user(1)

변경의 영향을 최소화하고 클래스가 독립적으로 테스트 될 수 있게한다.

낮은 결합도(국소화된 변경)

class UserInterface:
    def __init__(self, user_service):
        self.user_service = user_service

    def display_user(self, user_id):
        user = self.user_service.get_user(user_id)
        print(f"User: {user}")

class UserService:
    def __init__(self, user_repository):
        self.user_repository = user_repository

    def get_user(self, user_id):
        return self.user_repository.find_user(user_id)

class UserRepository:
    def find_user(self, user_id):
        # 데이터베이스에서 사용자 정보를 가져오는 로직
        return {"id": user_id, "name": "John Doe"}

# 사용 예시
user_repo = UserRepository()
user_service = UserService(user_repo)
ui = UserInterface(user_service)
ui.display_user(1)

의존성 주입.
클래스가 인터페이스나 추상 클래스를 통해 다른 객체에 의존하면 클래스가 구체적 구현이 아닌 추상화 된 인터페이스에 의존하게된다.
이를 통해 결합도를 낮추고 변경 시 영향을 최소화 할 수 있다.

결합도의 높낮음은 두가지 측면에서 평가한다.

의존성의 강도와 변경의 전파.
한 모듈이 다른 모듈에 얼마나 강하게 의존하고 있는가,
내부 구현 세부사항에 의존하거나, 구체적인 클래스를 직접 참여하고 있다면
결합도가 높다.
