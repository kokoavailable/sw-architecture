Two classes, components or modules are coupled when at least one of
them uses the other. The less these items know about each other, the
looser they are coupled.


클래스, 콤포넌트, 모듈등은 적어도 서로를 한번이라도 사용한다면, 결합됐다고 할 수 있다.
이 각각이 서로에 대해 최소한 으로 알고 있을때. 결합도는 느슨해진다.
(한 모듈이 다른 모듈에 얼마나 의존적인가 ?)

A component that is only loosely coupled to its environment can be more
easily changed or replaced than a strongly coupled component.

그 환경에 느슨하게 결합된 컴포넌트라면, 강하게 결합된 컴포넌트보다 더 쉽게 변경될 수 있다.

높은 예

class Database:
    def get_data(self):
        # 데이터베이스에서 데이터를 가져오는 로직
        return "Data from database"

class ReportGenerator:
    def __init__(self):
        self.database = Database()

    def generate_report(self):
        # 데이터베이스에 직접 의존
        data = self.database.get_data()
        return f"Report generated with {data}"

# 사용 예시
report_gen = ReportGenerator()
print(report_gen.generate_report())



낮은 예

class Database:
    def get_data(self):
        return "Data from database"

class MockDatabase:
    def get_data(self):
        return "Mock data for testing"

class ReportGenerator:
    def __init__(self, data_source):
        self.data_source = data_source

    def generate_report(self):
        # 인터페이스에만 의존
        data = self.data_source.get_data()
        return f"Report generated with {data}"

# 사용 예시
database = Database()
report_gen = ReportGenerator(database)
print(report_gen.generate_report())
