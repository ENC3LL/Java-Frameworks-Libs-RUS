[[JavaBase]]
%%Класс%%
class MyClass{
%%Поля класса%%
	String name;
	int code;
	char symb;
%%Конструктор%%
	MyClass(String name,int code,char symb){
		this.name=name;
		this.code=code;
		this.symb=symb;
	}
%%Переопределение метода toString()%%
	public String toString(){
		String res="Имя: "+name+"\n";
		res+="Число: "+code+"\n";
		res+="Символ: "+symb;
		return res;
	}
}
%%Главный класс%%
class Demo{
	public static void main(String[] args){
%%Создание объекта%%
		MyClass A=new MyClass("Первый",100,'A');
%%Автоматический вызов метода toString() %%
		System.out.println(A);
%%Создание объекта%%
		MyClass B=new MyClass("Второй",200,'B');
%%Автоматический вызов метода toString() %%
		String str="Создан новый объект\n"+B;
%%Проверка результата%%
		System.out.println(str);
	}
}

Результат выполнения программы

Имя: Первый
Число: 100
Символ: A
Создан новый объект
Имя: Второй
Число: 200
Символ: B