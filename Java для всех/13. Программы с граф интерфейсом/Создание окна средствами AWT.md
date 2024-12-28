[[JavaBase]]
%%Подключение пакетов%%
import java.awt.* ;
import java.awt.event.* ;
class Demo{
	public static void main(String[] args){
%%Создание объекта окна%%
		Frame wnd=new Frame("Окно AWT");
%%Размеры окна%%
		wnd.setSize(300,200);
%%Положение окна%%
		wnd.setLocation(500,400);
%%Добавление обработчика в окно%%
		wnd.addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent we){
%%Завершение выполнения программы %%
				System.exit(0);
			}
		});
%%Отображение окна%%
		wnd.setVisible(true);
	}
}

![[IMG_2395.jpeg]]