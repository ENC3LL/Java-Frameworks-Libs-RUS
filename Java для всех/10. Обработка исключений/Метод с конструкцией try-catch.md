[[JavaBase]]
import java.util.Random;
class Demo{
%%Статический метод%%
	static void generator(int a){
		int nums[]={-1,1};
		try{
			if(a== 1) a=a/(a-1);
			else nums[a]=200;
		}catch(ArrayIndexOut
		OfBoundsException e){
			System.out.println
			("Неправильный индекс: "+e);
		}
		finally{
			System.out.println("Ошибка происходит всегда!");
		}
	}
%%Главный метод%%
	public static void main(String[] args){
		Random r=new Random();
		int a,b;
		for(int k=1;k<=5;k++){
			System.out.println("Попытка №"+k);
			try{
				a=r.nextInt(3);
				b=100/a;
				System.out.println
				("b="+b);
%%Вызов статического метода%%
				generator(a);
			}catch(ArithmeticException e){
				System.out.println
				("Деление на ноль: "+e);
			}
		}
	}
}

Результат выполнения программы

Попытка №1
b=50
Неправильный индекс: java.lang.ArrayIndexOutOfBoundsException: 2
Ошибка происходит всегда!

Попытка №2
b=100
Ошибка происходит всегда!
Деление на ноль: java.lang.ArithmeticException: / by zero

Попытка №3
b=100
Ошибка происходит всегда!
Деление на ноль: java.lang.ArithmeticException: / by zero

Попытка №4
b=50
Неправильный индекс: java.lang.ArrayIndexOutOfBoundsException: 2
Ошибка происходит всегда!

Попытка №5
Деление на ноль: java.lang.ArithmeticException: / by zero