[[JavaBase]]
import java.awt.* ;
import java.awt.event.* ;
%%Класс для реализации окна%%
class MyFrame extends Frame{
	private int count=0;
	private String text="Нажмите кнопку \ "Число\ ": ";
%%Конструктор%%
	MyFrame(int x,int y){
		super();
%%Название окна%%
		setTitle("Окно с кнопками и меткой");
%%Положение и размеры окна%%
		setBounds(x,y,300,200);
%%Окно фиксированных размеров%%
		setResizable(false);
%%Обработчик для окна%%
		addWindowListener(new WindowAdapter(){
			public void windowClosing(WindowEvent we){
				System.exit(0);
			}
		});
%%Отключение менеджера компоновки для окна%%
		setLayout(null);
%%Создание объекта шрифта%%
		Font f=new Font(Font.DIALOG,
		Font.BOLD|Font.ITALIC,13);
%%Применение шрифта для окна%%
		setFont(f);
%%Создание панели%%
		Panel P=new Panel();
%%Положение и размеры панели%%
		P.setBounds(10,30,280,120);
%%Цвет фона для панели%%
		P.setBackground
		(Color.LIGHT_GRAY);
%%Определение менеджера компоновки для панели%%
		P.setLayout(new BorderLayout());
%%Создание метки%%
		Label L=new Label(text+count);
%%Выравнивание текста по центру метки %%
		L.setAlignment(Label.CENTER);
%%Цвет для шрифта метки%%
		L.setForeground(Color.BLUE);
%%Добавление метки в центр панели%%
		P.add(L,BorderLayout.CENTER);
%%Добавление панели в окно%%
		add(P);
%%Создание кнопки%%
		Button A=new Button("Закрыть");
%%Положение и размеры кнопки%%
		A.setBounds(40,160,90,30);
%%Обработчик для кнопки%%
		A.addActionListener(ae->System.exit(0));
%%Добавление кнопки в окно%%
		add(A);
%%Создание кнопки%%
		Button B=new Button("Число");
%%Обработчик для кнопки%%
		B.addActionListener(new ActionListener(){
			public void actionPerformed(ActionEvent ae){
				count++;
				if(count>3){
					B.setEnabled(false);
					L.setText("Кнопка \ "Число\ " заблокирована");
				}else{
					L.setText(text+count);
				}
			}
		});
%%Положение и размеры кнопки%%
		B.setBounds(170,160,90,30);
%%Добавление кнопки в окно%%
		add(B);
%%Отображение окна%%
		setVisible(true);
	}
}
%%Главный класс%%
class Demo{
	public static void main(String[] args){
%%Создание и отображение окна%%
		new MyFrame(400,300);
	}
}

![[IMG_2399.jpeg]]
![[IMG_2400.jpeg]]