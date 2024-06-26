Cohesion is the degree to which elements of a whole belong together.

응집도(일관성) 
응집도는 요소 그 전체가 얼마나 단일한 목적을 위해 서로 잘 존재하고 있는지를 나타내는 정도이다.

Methods and fields in a single class and classes of a component should have
high cohesion. 

한 클래스나 컴포넌트 안의 클래스들은 높은 응집도를 가지고 있어야 한다.

High cohesion in classes and components results in simpler,
more easily understandable code structure and design.

컴포넌트와 클래스의 높은 응집도는 더 간단하고, 코드 스트럭쳐와 디자인을 더 쉽게 이해할 수 있게 해준다.

높은 응집도:
클래스나 모듈 내의 모든 구성 요소들이 단일한 목적을 위해 잘 결합돼 있는 상태.

class DataProcessor:
    def __init__(self, data):
        self.data = data

    def clean_data(self):
        # 데이터를 정리하는 로직
        pass

    def analyze_data(self):
        # 데이터를 분석하는 로직
        pass

    def save_results(self):
        # 결과를 저장하는 로직
        pass


낮은 응집도:
클래스나 모듈 내의 구성 요소들이 여러 가지 다른 목적을 가지고 있는 상태

class MiscellaneousTasks:
    def clean_data(self):
        # 데이터를 정리하는 로직
        pass

    def send_email(self):
        # 이메일 전송 로직
        pass

    def connect_to_database(self):
        # 데이터베이스 연결 로직
        pass

    def generate_report(self):
        # 보고서 생성 로직
        pass