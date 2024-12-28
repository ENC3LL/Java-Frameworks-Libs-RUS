[[JavaBase]]
%%Подключение пакетов%%
import javax.swing.* ;
class Demo{
	public static void main(String[] args){
%%Создание объекта окна%%
		JFrame wnd=new JFrame("Окно Swing");
%%Размеры окна%%
		wnd.setSize(300,200);
%%Положение окна%%
		wnd.setLocation(500,400);
%%Реакция на нажатие системной пиктограммы%%
		wnd.setDefaultClose
		Operation(JFrame.EXIT_ON_CLOSE);
%%Отображение окна%%
		wnd.setVisible(true);
	}
}

![[IMG_2398.jpeg]]