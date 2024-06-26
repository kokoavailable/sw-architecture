Single Responsibility Principle (SRP)
A class should have one, and only one, reason to change.

클래스는 단 하나의 책임만 가져야하며, 변경은 그 책임에 의해서만 이루어 져야한다.

잘못된 예시

class User:
    def __init__(self, username, email):
        self.username = username
        self.email = email
    
    def save_to_database(self):
        # 데이터베이스에 사용자 정보를 저장하는 로직
        pass
    
    def send_welcome_email(self):
        # 환영 이메일을 보내는 로직
        pass


올바른 예시

class User:
    def __init__(self, username, email):
        self.username = username
        self.email = email

class UserRepository:
    def save_to_database(self, user):
        # 데이터베이스에 사용자 정보를 저장하는 로직
        pass

class EmailService:
    def send_welcome_email(self, user):
        # 환영 이메일을 보내는 로직
        pass

===============

Open Closed Principle (OCP)
You should be able to extend a class's behaviour without modifying it.
클래스의 동작을 수정하지 않고도 확장할 수 있어야 한다.

잘못된 예시
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class AreaCalculator:
    def calculate_area(self, shape):
        if isinstance(shape, Rectangle):
            return shape.area()
        # 새로운 도형을 추가하려면 여기에 코드를 추가해야 함

올바른 예시
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

class AreaCalculator:
    def calculate_area(self, shape: Shape):
        return shape.area()


==========

Liskov Substitution Principle (LSP)
Derived classes must be substitutable for their base classes.
파생 클래스는 기본 클래스를 대체할 수 있어야 한다.

잘못된 예시

class Bird:
    def fly(self):
        pass

class Ostrich(Bird):
    def fly(self):
        raise NotImplementedError("Ostriches can't fly")

올바른 예시

class Bird:
    def move(self):
        pass

class Sparrow(Bird):
    def move(self):
        print("Flying")

class Ostrich(Bird):
    def move(self):
        print("Running")
        
메서드 시그니처와 일반적인 계약을 정의하는 , 기반 클래스에서
서브 클래스는 이러한 계약을 준수하며, 자신만의 동작을 구현할 수 있어야 한다.
즉 기반 클래스와 동일한 동작을 할 필요는 없지만. 자신만의 move라는 메소드의 동작을 구현할 수 있어야한다.
즉 서브 클래스가 기반 클래스의 메서드를 오버라이딩 하더라도, 프로그램이 오류없이 정상 적으로 작동함으로써, 논리적 일관성이 유지 돼야 한다.

=======

Dependency Inversion Principle (DIP)
Depend on abstractions, not on concretions
구체적인 것에 의존하지 말고 추상화에 의존해야 한다.

고수준의 모듈(핵심 비즈니스 로직을 다루는 모듈)이 저수준의 모듈(DB등)에
의존하지 않아야 한다. 두 모듈 모두 추상화(인터페이스나 추상 클래스)에 의존하도록 하여 의존성의 방향을 역전시킨다.
이를 통해 결합도를 낮추고 코드의 재사용성과 유연성을 높일 수 있다.

전통적인 의존 관계 (의존성 역전 전)

class MySQLDatabase:
    def connect(self):
        pass

class UserRepository:
    def __init__(self):
        self.db = MySQLDatabase()  # 구체적인 구현에 의존

    def get_user(self, user_id):
        self.db.connect()
        # 사용자 정보를 가져오는 로직

고수준 모듈  --->  저수준 모듈
UserRepository  --->  MySQLDatabase

의존성 역전 후 

class DatabaseInterface:
    def connect(self):
        pass

class MySQLDatabase(DatabaseInterface):
    def connect(self):
        pass

class PostgreSQLDatabase(DatabaseInterface):
    def connect(self):
        pass

class UserRepository:
    def __init__(self, db: DatabaseInterface):
        self.db = db  # 추상화에 의존

    def get_user(self, user_id):
        self.db.connect()
        # 사용자 정보를 가져오는 로직

고수준 모듈  --->  추상화 <---  저수준 모듈
UserRepository  --->  DatabaseInterface <---  MySQLDatabase

이러한 구조에서는 고수준 모듈이 추상화에 의존하므로, 저수준 모듈을 더 쉽게 교체할 수 있다.

===========
Interface Segregation Principle (ISP)
Make fine grained interfaces that are client-specific.
클라이언트(인터페이스를 사용하는 코드나 클래스)에 특화된 세분화된 인터페이스를 만들어야 한다.

잘못된 예시

class WorkerInterface:
    def work(self):
        pass

    def eat(self):
        pass

class Worker(WorkerInterface):
    def work(self):
        print("Working")

    def eat(self):
        print("Eating")

class Robot(WorkerInterface):
    def work(self):
        print("Working")

    def eat(self):
        raise NotImplementedError("Robots don't eat")

올바른 예시


"클라이언트"는 객체 지향 설계에서 인터페이스를 사용하는 코드나 클래스를 의미합니다. 클라이언트는 특정 기능이나 서비스를 제공받기 위해 인터페이스를 호출하는 주체를 말합니다. 따라서 "클라이언트"는 서브 클래스와는 다릅니다. 서브 클래스는 상속 관계에 있는 클래스들 사이의 관계를 의미하는 것이고, 클라이언트는 인터페이스를 사용하는 측을 의미합니다.

클라이언트의 예시
클라이언트는 인터페이스나 클래스를 사용하는 모든 코드나 클래스가 될 수 있습니다. 예를 들어, 다음과 같은 경우를 생각해볼 수 있습니다.

예시 1: 프린터 인터페이스를 사용하는 클라이언트
python
Copy code
class Printable:
    def print(self, document):
        pass

class SimplePrinter(Printable):
    def print(self, document):
        print(f"Printing document: {document}")

class DocumentProcessor:
    def __init__(self, printer: Printable):
        self.printer = printer

    def process_and_print(self, document):
        # 문서를 처리하는 로직
        self.printer.print(document)  # Printable 인터페이스를 사용하는 클라이언트

# 사용 예시
printer = SimplePrinter()
processor = DocumentProcessor(printer)
processor.process_and_print("Hello, world!")
여기서 DocumentProcessor 클래스는 Printable 인터페이스를 사용하는 클라이언트입니다. DocumentProcessor는 Printable 인터페이스를 통해 프린터의 print 메서드를 호출합니다.

Interface Segregation Principle (ISP)의 예시
잘못된 예시 (ISP를 위반한 경우)
python
Copy code
class WorkerInterface:
    def work(self):
        pass

    def eat(self):
        pass

class Worker(WorkerInterface):
    def work(self):
        print("Working")

    def eat(self):
        print("Eating")

class Robot(WorkerInterface):
    def work(self):
        print("Working")

    def eat(self):
        raise NotImplementedError("Robots don't eat")
위 예시에서 Robot 클래스는 WorkerInterface를 구현하지만 eat 메서드를 구현할 수 없습니다. 이는 Robot 클래스가 필요하지 않은 메서드에 의존하게 만들어 ISP를 위반한 경우입니다. 여기서 Worker와 Robot 클래스는 WorkerInterface를 사용하는 클라이언트입니다.

올바른 예시 (ISP를 준수한 경우)
python
Copy code
class Workable:
    def work(self):
        pass

class Eatable:
    def eat(self):
        pass

class Worker(Workable, Eatable):
    def work(self):
        print("Working")

    def eat(self):
        print("Eating")

class Robot(Workable):
    def work(self):
        print("Working")


이렇게하면 클라이언트는 자신이 필요로 하는 메서드만 포함된 인터페이스를 사용해, 불필요한 의존성을 피할 수 있다.
이를 통해 시스템의 유연성과 유지보수성을 높일 수 있다.


==========

Classes Should be small


Small classes are easier to grasp. 
작은 클래스는 이해하기 쉽다. 
Classes should be smaller than about 100 lines of code.
클래스는 100줄 미만이여야 한다.
Otherwise, it is hard to spot how the class does its job and it probably does more than a single job.
그렇지 않으면 클래스가 어떤 일을 하는지 파악하기 어려우며, 아마 단일 작업 이상의 일을 수행할 것이다.

Do stuff or know others, but not both

Classes should either do stuff (algorithm, read data, write data, …) or orchestrate other classes. 
This reduces coupling and simplifies testing.
클래스는 어떤 작업을 수행하거나(알고리즘, 데이터 읽기, 데이터 쓰기 등), 다른 클래스를 조정하는 일 두가지중 하나의 역할만 가지고 있어야 한다.
(인터페이스와 서비스 등을 분리해라..)
이것은 결합도를 줄이며, 테스트를 단순화 한다.

의존성의 주입에는 크게 세가지가 있다.

생성자 주입

class DatabaseInterface:
    def connect(self):
        pass

class MySQLDatabase(DatabaseInterface):
    def connect(self):
        print("Connecting to MySQL database")

class UserRepository:
    def __init__(self, db: DatabaseInterface):
        self.db = db  # 생성자 주입

    def get_user(self, user_id):
        self.db.connect()
        print(f"Fetching user {user_id}")

# 의존성을 생성자를 통해 주입
mysql_db = MySQLDatabase()
user_repo = UserRepository(mysql_db)
user_repo.get_user(1)

메서드 주입

class DatabaseInterface:
    def connect(self):
        pass

class PostgreSQLDatabase(DatabaseInterface):
    def connect(self):
        print("Connecting to PostgreSQL database")

class UserRepository:
    def __init__(self):
        self.db = None

    def set_database(self, db: DatabaseInterface):
        self.db = db  # 메서드 주입

    def get_user(self, user_id):
        if self.db:
            self.db.connect()
            print(f"Fetching user {user_id}")
        else:
            print("Database not set")

# 의존성을 메서드를 통해 주입
user_repo = UserRepository()
postgres_db = PostgreSQLDatabase()
user_repo.set_database(postgres_db)  # 명시적으로 메서드 호출
user_repo.get_user(2)

필드 주입

class UserRepository:
    # 필드 주입을 위한 설정
    db = None

    def get_user(self, user_id):
        if self.db:
            self.db.connect()
            print(f"Fetching user {user_id}")
        else:
            print("Database not set")