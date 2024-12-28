[[JavaBase]]
Главное отличие между классами StringBuffer и StringBuilder состоит в том, что
при многопоточном программировании использование класса StringBuilder может
привести к проблемам. Поэтому его обычно используют в однопоточной модели.
Если же в программе используется многопоточная модель, то рекомендуется использовать класс StringBuffer. В прикладном плане работа с классом StringBuilder аналогична работе с классом StringBuffer

class Demo{
	public static void main(String[] args){
%%Текстовая строка%%
		StringBuilder A=new StringBuilder(30);
		System.out.println("Длина текста: "+A.length());
		System.out.println("Объем памяти: "+A.capacity());
%%В объект добавляется текст%%
		A.append("Изучаем Java");
		System.out.println(A);
%%Вставка подстроки в текст%%
		A.insert(8,"язык ");
		System.out.println(A);
%%Замена подстрок%%
		A.replace(0,3,"У").replace(2,4,"и");
		System.out.println(A);
%%Создание объекта класса String%%
		String B=A.toString();
		System.out.println(B);
	}
}

Результат выполнения программы

Длина текста: 0
Объем памяти: 30
Изучаем Java
Изучаем язык Java
Учим язык Java
Учим язык Java