package jdbcSQL;


import java.sql.*;
import java.util.*;

public class jdbc {

	public static void main(String[] args) {
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			
			//create user 'java'@'localhost' identified by 'Sumit@007' in mysql
			String url = "jdbc:mysql://localhost:3306/sumit";
			String usr = "java";
			String passwd ="Sumit@007";
		
			Connection conn = DriverManager.getConnection(url,usr,passwd);
			
			
			Scanner scan = new Scanner(System.in);
			
			
			Statement s = conn.createStatement();
			String s1 = "create table stud(name varchar(20),age int)";
			s.executeUpdate(s1);
			
			String query="";
			int ch;
			do {
				System.out.println("Enter choice \n 1.Insert\n 2.Select\n 3.Update\n 4.Delete \n5.Exit");
				ch=scan.nextInt();
				switch(ch) {
				case 1:
					System.out.println("Enter name and age");
					String n = scan.next();
					int ag = scan.nextInt();
					query = "insert into stud values('"+n+"','"+ag+"')";
					s.executeUpdate(query);
					System.out.println("Record is inserted");
					break;
				case 2:
					query = "select * from stud";
					ResultSet rs = s.executeQuery(query);
					while(rs.next()) {
						String name = rs.getString("name");
						int age = rs.getInt("age");
						System.out.println(name +" "+ age);
					}
					break;
				case 3:
					System.out.println("Enter name and what you want to update it to");
					String n1 = scan.next();
					String n2 = scan.next();
					query = "update stud set name ='"+n2+"' where name='"+n1+"'";
					s.executeUpdate(query);
					System.out.println("Record is updated");
					break;
				case 4:
					System.out.println("Enter name you want to delete");
					String n3 = scan.next();
					query = "delete from stud where name ='"+n3+"'";
					s.executeUpdate(query);
					System.out.println("Record is deleted");
					break;
				}
			}while(ch!=5);
			s.close();
			conn.close();
					
		}
		catch(Exception e){
			e.printStackTrace();
		}

	}

}
