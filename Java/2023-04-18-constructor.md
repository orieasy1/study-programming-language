<h1>생성자</h1>

우선 상속을 정리하기에 앞서 생성자를 먼저 정리한다.
클래스와 인스턴스에 대해 공부하면 생성자를 접하는 것이 일반적이지만 상속과 생성자 또한 밀접한 관련이 있다는 점을 꼭 기억했으면 좋겠다.
클래스 간의 계층구조와 초기화 과정을 관리하는데 관련이 있고, 상속된 클래스의 속성 초기화와 추가적인 초기화 작업을 위해 생성자 호출이 사용되기 때문이다.

1. 상속된 클래스의 초기화
하위 클래스는 상속을 통해 상위 클래스의 속성과 메소드를 상속받는다.
이때 상위클래스의 속성은 해당 클래스의 생성자를 통해 초기화된다.
하위 클래스의 객체를 생성하면, 상위 클래스의 생성자가 호출되어 상위 클래스의 속성을 초기화한다.
그 이후에 하위 클래스의 생성자가 호출되어 하위 클래스의 속성을 초기화한다.

2. 생성자 오버로딩과 초기화
생성자 오버로딩은 동일한 이름을 가지고 매개변수의 종류 또는 개수가 다른 여러 개의 생성자를 정의하는 것을 의미한다.
상속 관계에서 하위 클래스의 생성자는 상위 클래스의 자를 호출하여 상속된 속성을 초기화 한다. 이 때 생성자 오버로딩을 활용하여 다양한 초기화 방식을 지원할 수 있다.
상위 클래스의 생성자 호출은 super 키워드를 사용하여 명시적으로 수행된다.

<h3>생성자란 무엇인가?</h3>

생성자란 **클래스의 인스턴스(객체)를 초기화**하는 특별한 메소드이다.
인스턴스 초기화란 인스턴스를 생성할 때 해당 인스턴스의 속성(멤버 변수)를 초기화하는 작업이다.
멤버 변수는 인스턴스 변수 혹은 필드라고 불리며 인스턴스가 생성될 때마다 각각의 객체에 대해 개별적인 값을 가질 수 있다.
객체의 상태를 표현하고 객체가 가지는 데이터를 저장하는 용도로 사용된다.
예상치 못한 동작이 발생하는 것을 막고 속성들에 기본 값을 제공하여 인스턴스를 안정적으로 상용할 수 있도록 하기 위해 인스턴스 초기화가 필요하다.
멤버들을 초기화하는 것을 자바 문법으로 지정해 놓은 것이 생성자라 생각하면 된다.
<br><br>
생성자를 호출할 때는 new키워드와 함게 호출한다.
우리가 인스턴스를 생성할 대 해당 클래스의 생성자를 호출하여 객체를 초기화한다고 생각하면 된다.
인스턴스를 생성할 때 new 인스턴스명(); 이렇게 코드를 작성해주면되는데 ();가 읨하는 것이 인자를 전달받지 않은 생성자를 호출하는 것이다.
<br><br>
생성자는 우리가 명시적으로 정의하지 않아도 인스턴스를 생성하는 과정에서 자동으로 호출되면서 초기화가 이루어진다.
인스턴스 생성과정에서는 무조건 생성자가 호출되어야한다고 자바에서 문법적으로 정핺았기 때문에 사용자가 생성자를 작성하지 않는다면 자바 컴파일러가 자동으로 넣어준다.
이것을 우리는 **기본 생성자 혹은 디폴트 생성자**라고 부른다.

디폴트 생성자는 하는 일이 없고 비어있으며 인자값도 전달받지 않는다.
매개 변수가 존재하지 않는다는 뜻이다.
이렇게 자바 컴파일러가 생성자를 삽입시켜준다하더라도 좋은 클래스가 되기위해서는 가급적 생성자를 직접 정의시켜주는 것이 좋다.
<br><br>
반면 매개변수가 있는 생성자도 있는데, 이때는 객체를 생성하면서 초기화할 값들을 전달할 수 있다.
객체 생성과 동시에 초기값을 설정할 수 있다는 장점이 있다.
매개변수의 개수와 타입에 따라 여러 개의 생성자를 정의할 수 있는데 이를 **생성자 오버로딩**이라고 부른다.
<br><br><br>

<h3>생성자의 특징</h3>
생성자의 특징은 다음과 같다.

1. 생성자의 이름은 클래스 이름과 동일해야한다.
2. 생성자는 값을 반환하지 않고, 리턴타입도 표시하지 않는다.(return이 들어가면 안됨)
3. 객체를 생성할 때 new 키워드와 함께 호출된다.
4. 생성자는 클래스 내부에서만 선언될 수 있으며 상속되지 않는다.
5. 기본 생성자를 명시적으로 정의하지 않으면 자바는 기본적으로 매개변수가 엇는 기본 생성자를 자동으로 생성한다.

은행계좌 프로그램 예시
```java
class BankAccount {
  //멤버 변수
	String accNumber;	//계좌번호
	String ssNumber;	//주민번호
	int balance;	//예금잔액
	
	public BankAccount(String acc, String ss, int bal) {  //생성자
    //멤버 변수들을 
		accNumber = acc;	//acc로는 계좌번호 초기화
		ssNumber = ss;	//ss로는 주민번호 초기화
		balance = bal;	//bal로는 예금 잔액 초기화
	}
}

class BankAccountConstructor {
	public static void main(String[] args) {
		BankAccount lee = new BankAccount("3025101516711", "031025", 10000);
		//()안에 초기화 하고 싶은 값들을 적어주면 된다.

		BankAccount park = new BankAccount("123456789", "22102009", 10000);
	}
}
```

학생 정보를 출력하는 프로그램 예시
```java
class Student{
	String school = "서울과학기술대학교";
 	int studentID;
 	String name;
 	int age;
  
 	public Student(int studentID, String name, int age) {//생성자
  	this.studentID = studentID;
	this.name = namel
	this.age = age;
	}
	
	public void studentProfile() {
		System.out.println("---------------------------");
		System.out.println("학교 : " +school);
		System.out.println("학번 : " +studentID);
		System.out.println("이름 : " +name);
		System.out.println("나이 : " +age);
		System.out.println("---------------------------");
	}

 ```
 <br><br><br>
 
<h3>생성자 오버로딩</h3>
생성자 오버로딩에 있어서 꼭 알아야하는 키워드가 바로 this이다.
하지만 우리는 앞서 생성자 오버로딩이 아니라 인스턴스 변수에 접근하기 위해서 this 키워드를 사용했었다.
바로 위 예제에서도 나온 것 처럼 클래스 내에서 멤버 변수와 메서드의 매개 변수 이름이 동일할 경우, this를 사용하여 인스턴스 변수 참조할 수 있다.
학생정보를 출력하는 코드에서 생성자 { }안 코드를 보면 this.studentID = studentID;라는 코드를 발견할 수 있는데 이는 메소드의 매개변수로 전달 받은 studentID값을 클래스내 인스턴스 변수 studentID에 저장하겠다는 뜻이다.
<br><br>
메소드에 대해 공부할 때 메소드의 이름이 같아도 매개변수 선언이 다르면 메소드 호출문의 전달인자를 통해 메소드를 구분할 수 있기 때문에, 매개변수의 선언이 다르면 동일한 이름의 메소드 정의를 허용하는 것을 메소드 오버로딩이라고 배웠다.
그리고 생성자도 오버로딩의 대상이된다.
<br><br>
생성자 또한 이름이 같더라도 매개변수의 선언이 다르면 둘 이상 정의가 가능하다.
매개변수의 개수, 타입 또는 순서를 다르게 하여 **다양한 방식으로 객체를 초기화**할 수 있도록 한다.
생성자 오버로딩을 사용하는 이유는 다음과 같다.

1. 다양한 초기화 방법 제공<br>
생성자 오버로딩을 통해 매개변수의 종류나 개수를 다르게 함으로써 객체를 다양한 방식으로 초기화할 수 있다.
2. 편의성 제공<br>
생성자 오버로딩을 사용하면 매개변수의 조합에 따라 사용자가 편리하게 객체를 생성할 수 있다. 이를 통해 객체 생성코드의 가독성과 유연성을 높일 수 있다.

이해를 위해 예시를 들어보자면, 사람들의 정보를 저장해서 보여주는 예제를 작성할 때, 사람마다 정보 개수가 다를 수 있을 것이다. 여권이 있는 사람도 있을 것이고 없는 사람도 있을 텐데, 없는 사람은 여권 관련된 정보를 표시하지 않도록 생성자 오버로딩을 사용해서 표기할수 있다.

```java
class Person {
	private int regiNum;	//주민등록번호
	private int passNum;	//여권번호
	
	Person(int rnum, int pnum) {
		regiNum = rnum;
		passNum = pnum;
	}
	
	Person(int rnum) { //생성자 오버로딩
		regiNum = rnum;
		passNum = 0;
	}
	
	void showPersonalInfo() {
		System.out.println("주민등록번호: " + regiNum);
		if(passNum != 0) 
			System.out.println("여권 번호: " + passNum + '\n');
		else
			System.out.println("여권을 가지고 있지 않ㅅ습니다 \n");
	}
}

class ConOverloading {
	public static void main(String[] args) {
		//여권 있는 사람의 정보를 담은 인스턴스 생성
		Person kim = new Person(335577, 112233);
		
		//여권 없는 사람의 정보를 담은 인스턴스 생성
		Person lee = new Person(775544);
		
		kim.showPersonalInfo();
		lee.showPersonalInfo();
	}
}
```
<br><br>

위 코드에서 Person 클래스 부분을 다음과 같이 수정할 수 있다.

```java
class Person {
	private int regiNum;
	private int passNum;
	
	//여권이 있는 사람을 우히나 생성자
	Person(int rnum, int pnum) {
		regiNum = rnum;
		passNum = 0;
	}
	
	//여권 없는 사람을 위한 생성자
	Person(int rnum) {
		this(rnum, 0);
		//이 인스턴스 내에서 rnum과 0을 인자로 받는 다른 생성자를 호출
		//위에서 사용된 this는 오버로딩 된 다른 생성자를 의미
	}
	
	void showPersonalInfo() {
		System.out.println("주민등록번호: " + regiNum);
		if(passNum != 0) 
			System.out.println("여권 번호: " + passNum + '\n');
		else
			System.out.println("여권을 가지고 있지 않ㅅ습니다 \n");
	}
}
```

두번째 생성자가 어떻게 바뀌었는지에 대해 주목할 필요가 있다.

this(rnum, 0);

위 코드는 메소드를 호출하는 코드와 똑같이 생겼지만 실제로는 생성자를 호출하는 코드이다.
rnum,과 0을 인자로 받는 오버로딩된 다른 생성자를 호출하는 것이다.
이렇게 생성자를 정의하면 이 생성자는 초기화할 값을 전달받는 역할만 하고 실제 초기화는 첫번째로 정의된 생성자를 통해서 진행하는 형태가 된다.
this를 이용한 생성자의 정의를 이용하면 중복된 코드를 줄일 수 있다.
<br><br>
this를 한국어로 번역하면 '이'가 될 것이다.
자바에서 사용하는 this 키워드도 '이'와 관련되어있다. 기본적으로 this가 의미하는 것이 이 인스턴스라고 기억하면된다.
그래서 위 코드는 이 인스턴스에서 rnum과 0을 인자로 받는 다른 생성자를 호출하라는 코드가 되는 것이다.
this키워드를 이용한 다른 생성자 호출은 생성자 맨 첫 줄에만 올 수 있다는 점을 기억해야한다.
<br><br>
위 코드를 해석해보면 kim의 경우 주민등록번호와 여권번호를 모두 가지고 있고 이 두 인자를 매개변수로 받는 첫 번째 생성자에 저장된다.
인스턴스 lee의 경우 주민등록번호만 가지고 있고 주민등록번호 인자만 전달되는 두번째 생성자에 저장되게 된다.
this(rnum, 0);이라는 코드를 통해 lee의 rnum인 775544과 0df 둘다 인자로 받을 수 있는 처첫 번째 생성자를 호출하여 regiNum에는 775544를 저장하고 passNum에는 0을 저장하는 것이다.
두 인스턴스 모두 Person이라는 클래스를 바탕으로 생성되었으므로 우리가 코드를 볼때는 클래스 Person안에 생성자 코드를 보고 어떤 생성자가 호출되었는지 판단할 수 있다.

학생정보를 출력하는 코드
```java
class Student{
	//필드
	String school = "서울과학기술대학교";
	int studentID;
	String name;
	int age;

	//기본생성자
	public Student() {

	}

	//생성자 오버로딩
	public Student(int studentID) {
		this(studentID, null, 0);	//다른 생성자 호출
		//첫줄에만 올 수 있다.
	}

	public Student(int studentId, String name) {
		this(studentID, name, 0);
	}

	public Student(int studentID, String name, int age) {
		this.studentID = studentID;
		this.name =name;
		this.age = age;
	}
	
	public void studentProfile() {
		System.out.println("---------------------------");
		System.out.println("학교 : " +school);
		System.out.println("학번 : " +studentID);
		System.out.println("이름 : " +name);
		System.out.println("나이 : " +age);
		System.out.println("---------------------------");
	}
}

public class Ex02 {
	public static void main(String[] args) {
	Student student = new Student(22102009, "이지원", 21);
	
	student.studentProfile();
	}
}
```

<br><br>
문제 해결
1. Car class를 만든다.
2. 필드는 private String color; private int speed;로 한다.
3. 생성자에서 매개변수로 매개 값을 받아서 필드를 초기화한다.
4. 속도가 30미만이거나, 속도가 200을 초과할 경우 속도를 50으로 셋팅한다
5. 필드를 출력해주는 carProfile 메소드를 만들어서 객체 생성 시 생성자에게 메소드 호출을 하도록 한다.

```java
class Car {
	private String color;
	private int speed;
	
	public Car() {
	
	}
	
	public Car(String color, int speed) {
		this.color = color;
		
		if(speed < 30 || speed > 200) {
			System.out.println("속도는 30이상 200이하여야 합니다.");
			System.out.println("속도를 50으로 초기화합니다.");
			
			this.speed = 50;
		}else {
			this.speed =speed;
		}
		
		carProfile() {
			//메소드 호출
		}
	}
		
	public void carProfile() {
		System.out.println("내 자동차 색상: " + color);
		System.out.println("내 자동차 속도: " + speed);
	}
}

public class proSolve {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		
		System.out.println("생성할 자동차 색상은: ");
		String color = scan.next();
		
		System.out.println("생성할 자동차 속도는: ");
		int speed = scan.nextInt();
		
		new car(color, speed);
		
		scan.close();
	}
}
```

<br><br><br>
<h3>상속과 super키워드에 대한 언급</h3>
앞에서 상속과 생성자가 밀접한 관련이 있다고 언급했었다.
하위 클래스는 상속을 통해 상위 클래스의 속성과 메소드를 상속받는다.
상위 클래스는 해당 클래스의 생성자를 ㅌㅇ해 인스턴스를 초기화한다.
하위 클래스의 객체를 생성하면 먼저 상위클래스의 생성자가 생성되어 상위클래스의 속성을 초기화시키고 이후 하위클래스의 생성자를 호출하는 방식으로 초기화 되어야한다.
<br><br>
super 키워드는 상속관계에서 상위 클래스 즉 부모 클래스 멤버에 접근할 때 사용된다.
다음과 같이 상황을 정리 할 수 있다.

1. 부모 클래스의 생성자를 호출할 때 사용: super(매개변수);<br>
자식클래스 생성자에서 super 키워드를 사용하여 부모 클래스 생성자를 호출할 수 있다.
2. 부모 클래스 멤버 접근: super.메소드명;
3. 자식 클래스에서 super 키워들ㄹ 사용하여 부모 클래스 멤버(필드, 메소드)에 접근할 수 있다.

<br><br><br>

<h3>생성자와 메소드의 차이점</h3>
생성자의 모습을 살펴보면 메소드와 모습이 같다.
그래서 생성자를 생성자 메소드라고 부르기도 한다.
하지만 생성자와 메소드의 차이점은 분명하기 때문에 집고 넘어가야할 부분이 있다.
<br><br>
우선 메는드는 클래스 동작을 정의하는데 사용하는 반묜 생성자는 클래스의 일부로써 객체를 초기화하는데에 사용된다.
메소드는 객체 생성후에도 여러 번 호출이 가능하지만 생성자는 객체 생성시에만 new 키워드와 함께 호출이 가능하다.

생성자의 특징이자 생성자가 되기 위한 조건이기도한 부분은 꼭 기억해야한다.

1. 생성자의 이름은 클래스의 이름과 동일해야한다.
2. 생성자는 값을 반환하지 않고 반환형도 표시하지 않는다.





















