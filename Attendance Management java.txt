import javax.swing.*;
import javax.swing.table.DefaultTableModel;

import java.awt.*;

import java.sql.*;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class Javaui {

    public static void main(String args[])
    {
       new front();
      
    

    }
}

class Logo
{
    public Logo() 
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
        JLabel l=new JLabel("TEACHER NAME  :  RANJITH");
        l.setForeground( Color.YELLOW);
        JButton a=new JButton();
        JButton b=new JButton();
        JButton c=new JButton();
        JButton d=new JButton();
        a.setText("MY PROFILE");
        b.setText("LPU POLICY");
        c.setText("MARK ATTENDANCE");
        d.setText("Feedback");
        a.setBounds(550,370,150,30);
        b.setBounds(750,570,150,30);
        c.setBounds(750,370,150,30);
        d.setBounds(550,570,150,30);
        l.setBounds(650,270,200,120);
        f.add(a);
        f.add(b);
        f.add(c);
        f.add(d);
        f.add(l);
        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        d1.setText("LOGIN PAGE");
        d1.setBounds(675,700,150,50);
        d1.addActionListener(e -> {
            f.dispose();
            new front();
            
        });
        
         d.addActionListener(e -> {
         f.dispose();
          new Feedback();
          });

        c.addActionListener(e -> {
        f.dispose();
        new Attendance();
         });
       b.addActionListener(e -> {
        f.dispose();
        new Lpupolicy();
        });
        a.addActionListener(e -> {
            f.dispose();
            new Myprofile();
        });

    


        ImageIcon icon = new ImageIcon("C:/Users/skjaf/.vscode/java/lpubackground.jpg");
        JLabel l0= new JLabel(icon);
        l0.setBounds(0, 0, 3840,2160);
        f.add(l0);



        
        f.setSize(3840,2160);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}




class front
{
    public front()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());


          ImageIcon icon = new ImageIcon("C:/Users/skjaf/.vscode/java/personicon.jpeg");
          JLabel l0= new JLabel(icon);
          l0.setBounds(700, 10, 210,280);
            f.add(l0);



        JLabel l=new JLabel("TEACHER ID :");
        l.setBounds(625,300,120,50);
       l.setForeground( Color.BLUE);
        f.add(l);
        JLabel l2=new JLabel("TEACHER NAME :");
        l2.setBounds(625,400,120,50);
       l2.setForeground( Color.BLUE);
        f.add(l2);



        JLabel l1=new JLabel("PASSWORD        :");
        l1.setBounds(625,500,120,50);
        l1.setForeground( Color.BLUE);
        f.add(l1);

        JTextField t2=new JTextField();
        t2.setBounds(800,320,150,30);
        f.add(t2); 
        JTextField t3=new JTextField();
        t3.setBounds(800,420,150,30);
        f.add(t3); 

        JPasswordField t1=new JPasswordField();
        t1.setBounds(800,520,150,30);
        f.add(t1);
        
   


        JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("LOGIN");
        d.setBounds(625,600,150,50);


        d.addActionListener(e -> {

            String user1 = t2.getText();
            String pass1 = t1.getText();
           try
           {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/java","root","Jafer@123");
            Statement stmt=con.createStatement();
            ResultSet rs=stmt.executeQuery("select * from teacher where teacher_id='"+user1+"' and password='"+pass1+"'");
            if(rs.next())
            {
                f.dispose();
                new Logo();
                //String tt1=t3.getText();
              
            }
           
            else
            {
                JOptionPane.showMessageDialog(null,"Invalid Username or Password");
            }
           }catch(Exception e1)
           {
               System.out.println(e1);
           }
            
          });



        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        d1.setText("NEW USER");
        d1.setBounds(800,600,150,50);
        d1.addActionListener(e -> {
            f.dispose();
            new Setpassword();
            
          });

   
    f.add(p);
    

    f.getContentPane();

        f.setSize(3840,2160);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}




class Setpassword
{
    public Setpassword()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());

        JLabel l2=new JLabel("TEACHER ID:");
        l2.setBounds(615,300,120,50);
        f.add(l2);

        JTextField t3=new JTextField();
        t3.setBounds(820,320,150,30);
        f.add(t3);


        JLabel l=new JLabel("NEW PASSWORD:");
        l.setBounds(615,400,120,50);
        f.add(l);
        JLabel l1=new JLabel("CONFIRM PASSWORD:");
        l1.setBounds(615,500,160,50);
        f.add(l1);

        JTextField t2=new JTextField();
        t2.setBounds(820,420,150,30);
        f.add(t2); 

        JPasswordField t1=new JPasswordField();
        t1.setBounds(820,520,150,30);
        f.add(t1);

        ImageIcon icon = new ImageIcon("C:/Users/skjaf/.vscode/java/lpulogo.jpeg");
        JLabel l0= new JLabel(icon);
        l0.setBounds(675, 50, 231,127);
        f.add(l0); 

        JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("REGISTER");
        d.setBounds(750,650,150,50);
        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        f.add(p);
        d.addActionListener(e -> {
                try
                {
                    Class.forName("com.mysql.cj.jdbc.Driver");
                    Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/java","root","Jafer@123");
                   

                    Statement stmt=con.createStatement();
                    stmt.executeUpdate("create table if not exists teacher(teacher_id varchar(20),password varchar(20))");
                    String pass1 = t1.getText();
                    String pass2 = t2.getText();
                    String user1 = t3.getText();
                    if(pass1.equals("")|| pass2.equals("")|| user1.equals(""))
                    {
                        JOptionPane.showMessageDialog(null,"ALL FIELDS ARE MANDATORY"); 
                    } 
                    
                    
                       else if(pass1.equals(pass2))
                    {
                      
                        stmt.executeUpdate("insert into teacher values('"+user1+"','"+pass1+"')");
                        JOptionPane.showMessageDialog(null,"New User Registered Successfully");
                        f.dispose();
                        new front();

                    }
                
                else 
                    {
                        JOptionPane.showMessageDialog(null,"Password Mismatch");
                    }
                }
                catch(Exception e1)
                {
                    System.out.println(e1);
                }
            
          });

          
  

        f.setSize(3840,2160);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}




class Myprofile
{
    public  Myprofile()
{
        
        JFrame f=new JFrame("PROFILE");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
        JLabel l1=new JLabel("PERSONAL INFORMATION");
        l1.setBounds(50,250,300,50);
        l1.setFont(new Font("Verdana", Font.PLAIN, 20));
        f.add(l1);
        JLabel l2=new JLabel(" TEACHER NAME   :  RANJITH"); 
        l2.setBounds(50,350,350,50);
        f.add(l2);
        JLabel l3=new JLabel(" EXPERIENCE     :  4 YEARS"); 
        l3.setBounds(50,550,300,50);
        f.add(l3);


        JLabel l4=new JLabel("TEACHER ID        :  26108");
        l4.setBounds(50,450,150,50);
        f.add(l4);
         
    String data[][]={ {"MONDAY","26108","RANJITH","K21ST","10-12"},    
    {"TUESDAY","26108","RANJITH","K21ST","10-12"},    
    {"WEDNESDAY","26108","RANJITH","K21SP","10-12"},
    {"THURSDAY","26108","RANJITH","K21SP","10-12"},
    {"FRIDAY","26108","RANJITH","K21TR","10-12"}};    
String column[]={"DAY","TEACHER ID","NAME","SECTION","TIMMINGS"};         
JTable jt=new JTable(data,column);    
jt.setBounds(10,400,300,500);          
JScrollPane sp=new JScrollPane(jt); 
JButton d1=new JButton();
d1.setLayout(null);
f.add(d1);
d1.setText("HOME");
d1.setBounds(675,700,150,50);
d1.addActionListener( e -> {
    f.dispose();
    new Logo();
    
  });

f.add(sp);          
f.getContentPane();
f.setVisible(true); 
f.setSize(3840,2160);
f.setLocationRelativeTo(null);
f.setResizable(false);
f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 

}
}    




class Feedback
{
    public Feedback()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
        JLabel l=new JLabel("TEACHER NAME:");
        l.setBounds(615,200,120,50);
        f.add(l);
        JLabel l1=new JLabel("TEACHER ID:");
        l1.setBounds(615,300,120,50);
        f.add(l1);
        JLabel l2=new JLabel("COURSE NAME:");
        l2.setBounds(615,400,120,50);
        f.add(l2);
        JLabel l3=new JLabel("COURSE ID:");
        l3.setBounds(615,500,120,50);
        f.add(l3);
        JLabel l4=new JLabel("FEEDBACK:");
        l4.setBounds(615,600,120,50);
        f.add(l4);

        JTextField t2=new JTextField();
        t2.setBounds(800,220,150,30);
        f.add(t2); 

        JTextField t3=new JTextField();
        t3.setBounds(800,320,150,30);
        f.add(t3); 

        JTextField t4=new JTextField();
        t4.setBounds(800,420,150,30);
        f.add(t4); 

        JTextField t5=new JTextField();
        t5.setBounds(800,520,150,30);
        f.add(t5); 

        JTextField t6=new JTextField();
        t6.setBounds(800,620,350,30);
        f.add(t6); 

        JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("SUBMIT");
        d.setBounds(650,780,150,50);
        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        f.add(p);
        d.addActionListener(e -> {
                if(t2.getText().equals("")|| t2.getText().equals("")|| t3.getText().equals("")|| t4.getText().equals("")|| t5.getText().equals("")|| t6.getText().equals("")){
                    JOptionPane.showMessageDialog(null,"ALL FIELDS ARE MANDATORY");  
                    
                }
                else
                {
                    JOptionPane.showMessageDialog(null,"RESPONSE HAS BEEN SUCCESSFULLY RECORDED"); 
                    t2.setText("");
                    t3.setText("");
                    t4.setText("");
                    t5.setText("");
                    t6.setText("");
                    
                }
            
          });
          JButton d2=new JButton();
          d2.setLayout(null);
          f.add(d2);
          d2.setText("HOME");
          d2.setBounds(850,780,150,50);
          JButton d3=new JButton();
          d3.setLayout(null);
          f.add(d3);
          f.add(p);
          d2.addActionListener(e -> {
              f.dispose();
              new Logo();
              
            });

        f.setSize(3840,2160);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);
    }
}



class Attendance
{
    public Attendance()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();

 
        JLabel l0=new JLabel("ATTENDANCE MARKING SYSTEM");
        l0.setBounds(590,30,290,50);
        f.add(l0);


        JLabel l4=new JLabel("Course Name:");
        l4.setBounds(70,150,150,50);
        f.add(l4);

        JLabel l5=new JLabel("java");
        l5.setBounds(250,150,150,50);
        f.add(l5);

        JLabel l6=new JLabel("Section");
        l6.setBounds(70,230,150,50);
        f.add(l6);

        
        String[] courses = {"K21ST","K21SP","K21TR",};
        JComboBox<String> courseList = new JComboBox<>(courses);
        courseList.setBounds(250, 230, 90, 30);
        f.add(courseList);

        JLabel l7=new JLabel("Enter Student Details");
        l7.setBounds(70,350,350,50);
        l7.setFont(new Font("Verdana", Font.PLAIN, 20));
        f.add(l7);

        JLabel l8=new JLabel("Student Name:");
        l8.setBounds(70,420,150,50);
        f.add(l8);

        JTextField t1=new JTextField();
        t1.setBounds(250,440,150,30);
        f.add(t1);


        JLabel l9=new JLabel("Student id:");
        l9.setBounds(70,480,150,50);
        f.add(l9);

        JTextField t2=new JTextField();
        t2.setBounds(250,500,150,30);
        f.add(t2);

        JRadioButton r1=new JRadioButton("Present");
        r1.setBounds(70,550,100,30);
        f.add(r1);
        JRadioButton r2=new JRadioButton("Absent");
        r2.setBounds(200,550,100,30);
        f.add(r2);
        ButtonGroup bg=new ButtonGroup();
        bg.add(r1);
        bg.add(r2);

        JButton b=new JButton("Submit");
        b.setBounds(70,600,100,30);
        f.add(b);
        b.addActionListener(e -> {
            if(t1.getText().equals("")|| t2.getText().equals("")){
                JOptionPane.showMessageDialog(null,"ALL FIELDS ARE MANDATORY");  
                
            }
            else{
         
            try{
                String name=t1.getText();
                String id=t2.getText();
                String section=(String) courseList.getSelectedItem();
                String status="";
                if(r1.isSelected())
                {
                    status="Present";
                }
                else if(r2.isSelected())
                {
                    status="Absent";
                }
                else
                {
                    status="Not Marked";
                }

                Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/java","root","Jafer@123");
               
                Statement st=con.createStatement();
                String query1="create table if not exists attendance(name varchar(20),id varchar(20),section varchar(20),status varchar(20))";
                st.executeUpdate(query1);

                String query="insert into attendance values('"+name+"','"+id+"','"+section+"','"+status+"')";
                st.executeUpdate(query);
                JOptionPane.showMessageDialog(null,"Attendance Marked for : "+  name +" rollno: " + id +" is: " + status );

            }
            catch(Exception e1)
            {
                System.out.println(e1);
            }
        }
         
            
          });

        JButton b1=new JButton("Reset");
        b1.setBounds(200,600,100,30);
        f.add(b1);

        b1.addActionListener(e -> {
            t1.setText("");
            t2.setText("");
            bg.clearSelection();
            
          });

          JButton d=new JButton();
          d.setLayout(null);
          f.add(d);
          d.setText("HOME");
          d.setBounds(750,700,150,50);
          d.addActionListener(e -> {
              f.dispose();
              new Logo();
              
            });
        
        f.add(p);
        f.setSize(3840,2160);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setVisible(true);


    }
}




class Lpupolicy
{
    public Lpupolicy()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
    //    create label
    JLabel l1=new JLabel("LPU POLICIES");
    l1.setBounds(70,250,150,50);
    l1.setFont(new Font("Verdana", Font.PLAIN, 20));
    f.add(l1);

    JButton d1=new JButton();
    d1.setLayout(null);
    f.add(d1);
    d1.setText("UMC CASE");
    d1.setBounds(90,350,150,50);
    JButton d2=new JButton();
    d2.setLayout(null);
    f.add(d2);
    d2.setText("IN-DESCIPLINE CASE ");
    d2.setBounds(90,450,170,50);
    d1.addActionListener(e -> {
        f.dispose();
        new UMCCASE();
        
      });
      d2.addActionListener(e -> {
        f.dispose();
        new IDcase();
      });
      JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("HOME");
        d.setBounds(750,700,150,50);
        d.addActionListener(e -> {
            f.dispose();
            new Logo();
            
          });
      f.add(p);
      f.setSize(3840,2160);
      f.setLocationRelativeTo(null);
      f.setResizable(false);
      f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      f.setVisible(true);
    }
}




class UMCCASE
{
    public UMCCASE()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
        JLabel l=new JLabel("STUDENT NAME:");
        l.setBounds(615,200,120,50);
        f.add(l);
        JLabel l1=new JLabel("STUDENT ID:");
        l1.setBounds(615,300,120,50);
        f.add(l1);
        JLabel l2=new JLabel("BRANCH NAME:");
        l2.setBounds(615,400,120,50);
        f.add(l2);
        JLabel l4=new JLabel("REASON:");
        l4.setBounds(615,500,120,50);
        f.add(l4);

        JTextField t2=new JTextField();
        t2.setBounds(800,220,150,30);
        f.add(t2); 

        JTextField t3=new JTextField();
        t3.setBounds(800,320,150,30);
        f.add(t3); 

        JTextField t4=new JTextField();
        t4.setBounds(800,420,150,30);
        f.add(t4); 

        JTextField t5=new JTextField();
        t5.setBounds(800,520,150,30);
        f.add(t5);
        JLabel l7=new JLabel("UMC CASE :");
        l7.setBounds(100,150,150,50);
        l7.setFont(new Font("Verdana", Font.PLAIN, 20));
        f.add(l7); 
        JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("SUBMIT");
        d.setBounds(600,700,150,50);
        d.addActionListener(e -> {
                if(t2.getText().equals("")|| t3.getText().equals("")|| t4.getText().equals("")|| t5.getText().equals("")){
                    JOptionPane.showMessageDialog(null,"ALL FIELDS ARE MANDATORY");  
                    
                }
                else
                {
                    JOptionPane.showMessageDialog(null,"UN-FAIR MEANS CASE HAS BEEN RECORDED AGANIST"+t2.getText()+" STUDENT ID "+t3.getText());
                    t2.setText("");
                    t3.setText("");
                    t4.setText("");
                    t5.setText("");
                }
            
          });
        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        d1.setText("LPU POLICY");
        d1.setBounds(850,700,150,50);
        d1.addActionListener(e -> {
            f.dispose();
            new Lpupolicy();
            
          });
          f.add(p);
          f.setSize(3840,2160);
          f.setLocationRelativeTo(null);
          f.setResizable(false);
          f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          f.setVisible(true);
  
    }
}





class IDcase
{
    public IDcase()
    {
        JFrame f=new JFrame("Student Attendance System");
        JPanel p=new JPanel();
        p.setLayout(new FlowLayout());
        JLabel l=new JLabel("STUDENT NAME:");
        l.setBounds(615,200,120,50);
        f.add(l);
        JLabel l1=new JLabel("STUDENT ID:");
        l1.setBounds(615,300,120,50);
        f.add(l1);
        JLabel l2=new JLabel("BRANCH NAME:");
        l2.setBounds(615,400,120,50);
        f.add(l2);
        JLabel l4=new JLabel("REASON:");
        l4.setBounds(615,500,120,50);
        f.add(l4);

        JTextField t2=new JTextField();
        t2.setBounds(800,220,150,30);
        f.add(t2); 

        JTextField t3=new JTextField();
        t3.setBounds(800,320,150,30);
        f.add(t3); 

        JTextField t4=new JTextField();
        t4.setBounds(800,420,150,30);
        f.add(t4); 

        JTextField t5=new JTextField();
        t5.setBounds(800,520,150,30);
        f.add(t5); 
        JLabel l7=new JLabel("INDESCPLINE CASE :");
        l7.setBounds(100,150,300,50);
        l7.setFont(new Font("Verdana", Font.PLAIN, 20));
        f.add(l7);

        JButton d=new JButton();
        d.setLayout(null);
        f.add(d);
        d.setText("SUBMIT");
        d.setBounds(600,700,150,50);
        d.addActionListener(e -> {
          if(t2.getText().equals("")|| t3.getText().equals("")|| t4.getText().equals("")|| t5.getText().equals("")){
                    JOptionPane.showMessageDialog(null,"ALL FIELDS ARE MANDATORY");  
                    
                }
                else
                {
                    JOptionPane.showMessageDialog(null,"IN-DESCIPLINE CASE HAS BEEN RECORDED AGANIST"+t2.getText()+" STUDENT ID"+t3.getText());
                    t2.setText("");
                    t3.setText("");
                    t4.setText("");
                    t5.setText("");
                }
            });
        JButton d1=new JButton();
        d1.setLayout(null);
        f.add(d1);
        d1.setText("LPU POLICY");
        d1.setBounds(850,700,150,50);
        d1.addActionListener(e -> {
           f.dispose();
           new Lpupolicy();     
            
          });
          f.add(p);
          f.setSize(3840,2160);
          f.setLocationRelativeTo(null);
          f.setResizable(false);
          f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          f.setVisible(true);
  
    }
}
