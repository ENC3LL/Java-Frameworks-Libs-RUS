[[JavaBase]]
class Demo{
	public static void main(String[] args){
		int sum=0,i=1,n=100;
%%Оператор цикла%%
		while(i<=n){
			sum+=i;
			i+=2;
		}
		System.out.println(
			"Сумма нечетных чисел от 1 до "+n+": "+sum
		);
	}
}

Результат выполнения программы
Сумма чисел от 1 до 100: 5050