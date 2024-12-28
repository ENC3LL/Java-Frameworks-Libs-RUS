[[JavaBase]]
class Demo{
%%Статический метод для отображения информации об объекте%%
	static void show(StringBuffer txt){
		System.out.println("Длина текста: "+txt.length());
		System.out.println("Объем памяти: "+txt.capacity());
	}
%%Главный метод%%
	public static void main(String[] args){
%%Объекты класса StringBuffer%%
		StringBuffer A=new StringBuffer("Изучаем Java");
		StringBuffer B=new StringBuffer();
		StringBuffer C=new StringBuffer(30);
%%Параметры объектов%%
		System.out.println("Объект A:");
		show(A);
		System.out.println("Объект B:");
		show(B);
		System.out.println("Объект C:");
		show(C);
%%Вставка подстроки%%
		A.insert(8,"C++ и ");
		System.out.println(A);
%%Замена подстроки%%
		A.replace(8,11,"Python");
		System.out.println(A);
		System.out.println("Объект A:");
		show(A);
%%Изменение объема памяти%%
		A.trimToSize();
		show(A);
%%Изменение длины текста%%
		A.setLength(14);
		System.out.println(A);
		show(A);
%%Увеличение объема памяти%%
		A.ensureCapacity(50);
		show(A);
%%Инверсия текста%%
		A.reverse();
		System.out.println(A);
		System.out.println("Объект B:");
%%Добавление подстроки%%
		B.append("Python и Basic");
		System.out.println(B);
%%Удаление подстроки%%
		B.delete(1,10);
		System.out.println(B);
%%Удаление символа%%
		B.deleteCharAt(3);
		System.out.println(B);
%%Добавление символов%%
		B.append(‘a');
		B.append('l');
		System.out.println(B);
	}
}

Результат выполнения программы 

Объект A:
Длина текста: 12
Объем памяти: 28
Объект B:
Длина текста: 0
Объем памяти: 16
Объект C:
Длина текста: 0
Объем памяти: 30
Изучаем C++ и Java
Изучаем Python и Java
Объект A:
Длина текста: 21
Объем памяти: 28
Длина текста: 21
Объем памяти: 21
Изучаем Python
Длина текста: 14
Объем памяти: 21
Длина текста: 14
Объем памяти: 50
nohtyP меачузИ
Объект B:
Python и Basic
Pasic
Pasc
Pascal