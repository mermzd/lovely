# lovely
package view;

import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JTextField;
import javax.swing.JLabel;
import javax.swing.JComboBox;
import javax.swing.DefaultComboBoxModel;
import javax.swing.JButton;
import javax.swing.JTable;
import javax.swing.table.DefaultTableModel;

import model.students;

import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.awt.event.ActionEvent;

public class main {

	private JFrame frame;
	private JTextField txtName;
	private JTextField txtGrade;
	private JTable table;
	private students s;
	private int x = 0 ;
	private int y = 0;
	private int r = 0;
	private int a = 0;
	private int y1 = 0;
	private int max=-1, n7=0;
	String[] names = {" ", " "," "," "," "," "};
	int[] numbers= new int[30];
	private int t=0;
	int ra = 0;
	int ro=0;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					main window = new main();
					window.frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the application.
	 */
	public main() {
		s = new students();
		initialize();
	}

	/**
	 * Initialize the contents of the frame.
	 */
	private void initialize() {
		frame = new JFrame();
		frame.setBounds(100, 100, 657, 290);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.getContentPane().setLayout(null);
		
		txtName = new JTextField();
		txtName.setBounds(33, 27, 186, 20);
		frame.getContentPane().add(txtName);
		txtName.setColumns(10);
		
		JLabel lblStudintNeim = new JLabel("student name");
		lblStudintNeim.setBounds(37, 11, 91, 14);
		frame.getContentPane().add(lblStudintNeim);
		
		txtGrade = new JTextField();
		txtGrade.setBounds(178, 98, 57, 20);
		frame.getContentPane().add(txtGrade);
		txtGrade.setColumns(10);
		
		JComboBox cB1 = new JComboBox();
		cB1.setModel(new DefaultComboBoxModel(new String[] {" "}));
		cB1.setBounds(33, 98, 135, 20);
		frame.getContentPane().add(cB1);
		
		JButton btnAddStudint = new JButton("ADD student");
		btnAddStudint.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				String h = txtName.getText();
				s.AddStudent(h);
				txtName.setText(null);
				table.setValueAt(s.showName(r), x, y);
				if(x<5) {
					x++;
				}
				else { 
					x=0;
				}
				names[r] = h;
				if(r<30) {
					r++;
				}
				cB1.addItem(h);
				}
		});
		btnAddStudint.setBounds(33, 58, 89, 23);
		frame.getContentPane().add(btnAddStudint);
	
		JButton btnAddGreid = new JButton("ADD grade");
		btnAddGreid.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				String namus = (String) cB1.getSelectedItem();
				s.AddGrade(namus, Integer.parseInt(txtGrade.getText()));
				for(int i =0;i<names.length;i++) {
					if(namus==names[i]) {
						a=i;
					}
				}
				if(y1>=4) {
					y1=1;
				}
				if(table.getModel().getValueAt(a,y1)!=null) {
					y1++;
				}
				table.setValueAt(s.showGrade(a), a, y1);
				numbers[t]=Integer.parseInt(txtGrade.getText());
				t++;
				txtGrade.setText(null);
			}
		});
		btnAddGreid.setBounds(33, 129, 89, 23);
		frame.getContentPane().add(btnAddGreid);
		
		table = new JTable();
		table.setModel(new DefaultTableModel(
			new Object[][] {
				{null, null, null, null, null},
				{null, null, null, null, null},
				{null, null, null, null, null},
				{null, null, null, null, null},
				{null, null, null, null, null},
				{null, null, null, null, null},
			},
			new String[] {
				"New column", "New column", "New column", "New column", "New column"
			}
		));
		table.setBounds(293, 30, 309, 96);
		frame.getContentPane().add(table);
		
		JLabel lblGreids = new JLabel("GREIDS");
		lblGreids.setBounds(293, 11, 46, 14);
		frame.getContentPane().add(lblGreids);
		
		JLabel beast = new JLabel(" ");
		beast.setBounds(391, 148, 211, 14);
		frame.getContentPane().add(beast);
		
		JLabel nof7 = new JLabel(" ");
		nof7.setBounds(392, 182, 211, 14);
		frame.getContentPane().add(nof7);
	
		
		JButton btnBeasr = new JButton("beAst");
		btnBeasr.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				
				for (int j=0; j<6;j++){
					
				if (j==0){
			        int max2 = -1;
			        
			        for(int i = 1; i < 5; i++)
			        	
			        {
			          int val = Integer.parseInt(table.getValueAt(0, i).toString());
			          if(val > max2)
			          {
			        	  int temp=val;
			        	  val=max2;
			        	  max2=temp;
			             
			          }
			        }
			        beast.setText(Integer.toString(max2));
			        
				}
				
				else if (j==1){
			    
			        	int max3 = -1;
			        
			        for(int i = 1; i < 5; i++)
			        	
			        {
			          int val1 = Integer.parseInt(table.getValueAt(1, i).toString());
			          if(val1 > max3)
			          {
			        	  int temp=val1;
			        	  val1=max3;
			        	  max3=temp;
			             
			          }
			        }
			        beast.setText(Integer.toString(max3));
			       
				}
				
				else if (j==2){
				    
		        	int max4 = -1;
		        
		        for(int i = 1; i < 5; i++)
		        	
		        {
		          int val1 = Integer.parseInt(table.getValueAt(2, i).toString());
		          if(val1 > max4)
		          {
		        	  int temp=val1;
		        	  val1=max4;
		        	  max4=temp;
		             
		          }
		        }
		        beast.setText(Integer.toString(max4));
		       
			}
			        
				//beast.setText(String.valueOf(s.getMaxOfRow()));
				
			}}});
		btnBeasr.setBounds(293, 144, 89, 23);
		frame.getContentPane().add(btnBeasr);
		
		JButton btnOfs = new JButton("\u2116 of 7s");
		btnOfs.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				for(int i=0;i<numbers.length;i++) {
					if(numbers[i]==7) {
						n7++;
					}
				}
				nof7.setText(""+n7);
			}
		});
		btnOfs.setBounds(293, 178, 89, 23);
		frame.getContentPane().add(btnOfs);
	}
	
	
}
