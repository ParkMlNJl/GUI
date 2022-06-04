# GUI
import java.awt.event.*; 
import javax.swing.*;

public class RadioButtonEvent extends JFrame implements ItemListener{

	JLabel Lb; 

	JPanel p1, p2; 

	JTextField tf1, tf2; 
	JRadioButton Rb1, Rb2, Rb3, Rb4;
 	ButtonGroup grp; 

 	public RadioButtonEvent(){ // RadioButtonEvent를 메서드로 재선언합니다.

		setTitle("라디오버튼 이벤트2"); // Title을 화면에서 출력된 대로 정합니다.

		Lb = new JLabel(""); // 라벨을 생성합니다. 연산의 결과를 출력할 라벨입니다.

		tf1 = new JTextField(10); // 텍스트필드를 두개 선언합니다.
		tf2 = new JTextField(10); // tf1, tf2 는 두 입력값을 받을 것입니다.

		Rb1 = new JRadioButton("더하기"); // 라디오버튼을 생성합니다.
		Rb2 = new JRadioButton("빼기"); // Rb1은 더하기, Rb2는 빼기
		Rb3 = new JRadioButton("곱하기"); // Rb3는 곱하기, Rb4는 나누기로 적어줍니다.
		Rb4 = new JRadioButton("나누기"); // 기능은 아래에서 구현합니다.

		Rb1.addItemListener(this);
		Rb2.addItemListener(this); 
		Rb3.addItemListener(this);
		Rb4.addItemListener(this);

		grp = new ButtonGroup(); // 버튼 그룹을 생성합니다.

		grp.add(Rb1); // 4개의 라디오버튼을
		grp.add(Rb2); // 그룹으로 묶어줍니다.
		grp.add(Rb3);
		grp.add(Rb4);

		p1 = new JPanel(); // 판넬을 두개 생성합니다.
		p2 = new JPanel(); 
 
		p1.add(tf1); // p1 판넬에는
		p1.add(tf2); // 텍스트필드 2개를 넣고

		p2.add(Rb1); // p2 판넬에는
		p2.add(Rb2); // 라디오버튼 4개를 넣어줍니다.
		p2.add(Rb3);
		p2.add(Rb4);
		
        add("North", p1); // p1 판넬은 위쪽에 배치하고
		add("Center", p2); // p2 판넬은 가운데에 배치하고
		add("South", Lb); // 라벨은 맨 아래쪽에 배치합니다.

		setSize(300, 300); // 프레임의 사이즈는 가로 300, 세로 300으로 합니다.
		setVisible(true); // 프레임을 보일수 있도록 setVisible을 true로 잡습니다.

	} // end RadioEvnet()

	public void itemStateChanged(ItemEvent e){ // 텍스트필드와 라디오버튼의 이벤트처리를 위한 메서드입니다.

 		double d1, d2, d3; // double 타입 변수 d1, d2, d3를 선언합니다.
        
		d1 = Double.parseDouble(tf1.getText()); // tf1에서 입력받은 값을 double 타입으로 형변환 후 d1에 대입합니다.
		d2 = Double.parseDouble(tf2.getText()); // tf2에서 입력받은 값을 double 타입으로 형변환 후 d2에 대입합니다.

 		if(Rb1.isSelected()){ // Rb1을 체크한 경우
 			d3 = d1 + d2; // 두 값에 대하여 덧셈 연산을 진행 후 결과를 d3에 저장합니다.
			Lb.setText(d1 + "+" + d2 + "=" + d3); // 라벨에 덧셈 연산 결과를 출력합니다.
		}
 
		if(Rb2.isSelected()){ // Rb2를 체크한 경우
 			d3 = d1 - d2; // 두 값에 대하여 뺄셈 연산을 진행 후 결과를 d3에 저장합니다.
 			Lb.setText(d1 + "-" + d2 + "=" + d3); // 라벨에 뺄셈 연산 결과를 출력합니다.
		}
        
 		if(Rb3.isSelected()){ // Rb3을 체크한 경우
 			d3 = d1 * d2; // 두 값에 대하여 곱셈 연산을 진행 후 결과를 d3에 저장합니다.
			Lb.setText(d1 + "*" + d2 + "=" + d3); // 라벨에 곱셈 연산 결과를 출력합니다.
 		}

 		if(Rb4.isSelected()){ // Rb4를 체크한 경우
			d3 = d1 / d2; // 두 값에 대하여 나눗셈 연산을 진행 후 결과를 d3에 저장합니다.
			Lb.setText(d1 + "/" + d2 + "=" + d3); // 라벨에 나눗셈 연산 결과를 출력합니다.
		}
        
	} // end itemStateChange

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		RadioButtonEvent rbe = new RadioButtonEvent(); 
	} // end main
    
} // end class
