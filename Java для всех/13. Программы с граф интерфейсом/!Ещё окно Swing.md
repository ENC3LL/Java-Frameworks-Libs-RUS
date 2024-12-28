[[JavaBase]]
%%Подключение пакетов%%
import javax.swing.* ;
%%Класс для создания окна%%
class MyFrame extends JFrame{
%%Конструктор%%
	MyFrame(String name){
%%Вызов конструктора суперкласса%%
		super(name);
%%Размеры окна%%
		setSize(300,200);
%%Положение окна%%
		setLocation(500,400);
%%Реакция на нажатие системной пиктограммы%%
		setDefaultClose
		Operation(EXIT_ON_CLOSE);
%%Отображение окна%%
		setVisible(true);
	}
}
%%Главный класс%%
class Demo{
	public static void main(String[] args){
%%Создание и отображение окна%%
		new MyFrame("Окно Swing");
	}
}

![[IMG_2398.jpeg]]