[[JavaBase]]
import javax.swing.* ;
import java.awt.* ;
import java.awt.event.* ;
class MyFrame extends JFrame{
	private int count=0;
	private String text="Нажмите кнопку \ "Число\ ": ";
	MyFrame(int x,int y){
		super();
		setTitle("Окно с кнопками и меткой");
		setBounds(x,y,300,200);
		setResizable(false);
		setDefaultClose
		Operation(EXIT_ON_CLOSE);
		setLayout(null);
		Font f=new Font(Font.DIALOG,
		Font.BOLD|Font.ITALIC,13);
		JPanel P=new JPanel();
		P.setBounds(10,10,275,120);
		P.setBackground
		(Color.LIGHT_GRAY);
		P.setLayout(new BorderLayout());
		JLabel L=new JLabel(text+count);
		L.setHorizontal
		Alignment(JLabel.CENTER);
		L.setForeground(Color.BLUE);
		L.setFont(f);
		P.add(L,BorderLayout.CENTER);
		add(P);
		JButton A=new JButton("Закрыть");
		A.setBounds(30,135,100,30);
		A.setFont(f);
		A.addActionListener(ae->System.exit(0));
		add(A);
		JButton B=new JButton("Число");
		B.setFont(f);
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
		B.setBounds(170,135,100,30);
		add(B);
		setVisible(true);
	}
}
class Demo{
	public static void main(String[] args){
		new MyFrame(400,300);
	}
}

![[IMG_2414.jpeg]]
![[IMG_2415.jpeg]]