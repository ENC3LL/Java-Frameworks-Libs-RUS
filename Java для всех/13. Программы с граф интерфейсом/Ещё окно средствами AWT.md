[[JavaBase]]
%%Подключение пакетов%%
import java.awt.* ;
import java.awt.event.* ;
%%Класс для создания окна%%
class MyFrame extends Frame{
%%Конструктор%%
	MyFrame(String name){
%%Вызов конструктора суперкласса%%
		super(name);
%%Размеры окна%%
		setSize(300,200);
%%Положение окна%%
		setLocation(500,400);
%%Добавление обработчика в окно%%
		addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent we){
%%Завершение выполнения программы %%
				System.exit(0);
			}
		});
%%Отображение окна%%
		setVisible(true);
	}
}
%%Главный класс%%
class Demo{
	public static void main(String[] args){
%%Создание и отображение окна%%
		new MyFrame("Окно AWT");
	}
}

![[IMG_2395.jpeg]]