# ACD_JAVAB2_Session_5_Assignment_3
package Session5_Assignment;

abstract class Employee {
	int empId;
	String empName;
	int total_leaves;
	//double total_salary;
	public Employee(int empId, String empName, int total_leaves) {
		super();
		this.empId = empId;
		this.empName = empName;
		this.total_leaves = total_leaves;
//		this.total_salary = total_salary;
	}
	
	public abstract void calculate_balance_leaves(); 	
	public abstract  boolean avail_leave(int no_of_leaves, char type_of_leave);
	public abstract void calculate_salary();

}

package Session5_Assignment;

public class PermanentEmp  extends Employee{
	int paid_leave, sick_leave, casual_leave;
	double basic, hra,pfa;
	 int no_of_leaves;
	 char type_of_leave;
	
	public PermanentEmp(int empId, String empName, int total_leaves, int paid_leave,
			int sick_leave, int casual_leave, double basic) {
		super(empId, empName, total_leaves);
		this.paid_leave = paid_leave;
		this.sick_leave = sick_leave;
		this.casual_leave = casual_leave;
		this.basic = basic;
		
	}
	@Override
	public void calculate_balance_leaves() {
		// TODO Auto-generated method stub
		int bal_leaves = total_leaves-(paid_leave + sick_leave + casual_leave);
		System.out.println("Balance Leaves:"+ bal_leaves);
		
	}
	@Override
	public boolean avail_leave(int no_of_leaves, char type_of_leave) {
		// TODO Auto-generated method stub
	  this.no_of_leaves = no_of_leaves;
	  this.type_of_leave = type_of_leave;
	  int avail_leavepl = total_leaves - paid_leave;
	  int avail_leavesk = total_leaves - sick_leave;
	  int avail_leavecl = total_leaves - casual_leave;
	  
	 if (avail_leavepl <=12 && type_of_leave == 'P'){
		 System.out.println("available balance PL:"+ avail_leavepl);
		 return true;
	 }
	 else if (avail_leavesk <=12 && type_of_leave == 'S'){
		 System.out.println("available balance sk:"+ avail_leavesk);
		return true;
	 }
	 if (avail_leavecl  <=12 && type_of_leave == 'C'){
		 System.out.println("available balance sk:"+ avail_leavecl);
		 return true;
	 }
	 else{
		 System.out.println("No leaves available");
		return false;
	 }
		
	}
	@Override
	public void calculate_salary() {
		// TODO Auto-generated method stub
		
		double total_salary = basic + 0.5 * basic - 0.12 * basic;
		System.out.println("Perm emp Salary:"+ total_salary );
		
	}
	
}
package Session5_Assignment;

public class TemporaryEmp extends Employee {

	public TemporaryEmp(int empId, String empName, int total_leaves) {
		super(empId, empName, total_leaves);
		// TODO Auto-generated constructor stub
	}

	@Override
	public void calculate_balance_leaves() {
		// TODO Auto-generated method stub
		System.out.println(" balance leaves calculation not needed" );
		
	}

	@Override
	public boolean avail_leave(int no_of_leaves, char type_of_leave) {
		// TODO Auto-generated method stub
		System.out.println(" No leaves leaves are allowed for temp employee" );
		return false;
	}

	@Override
	public void calculate_salary() {
		// TODO Auto-generated method stub
		double total_salary = 15000.00;
		System.out.println(" No salary calculation for Temp employees  fixed with Temp emp Salary:" + total_salary );
		
	}
 
	
}

package Session5_Assignment;

import java.util.Scanner;

public class MainEmployee {

	int total_leaves;
	//double total_salary;

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in);		
		System.out.println("Enter EmpId:");
		int empId = sc.nextInt();

		System.out.println("Enter Empname:");
		String empName = sc.next();

		System.out.println("Enter total leaves:");
		int total_leaves = sc.nextInt();
		
		System.out.println("Enter paid leaves:");
		int paid_leave = sc.nextInt();
		System.out.println("Enter sick leaves:");
		int sick_leave = sc.nextInt();
		System.out.println("Enter casual leaves:");
		int casual_leave = sc.nextInt();
		System.out.println("Enter basic salary:");
		double basic = sc.nextDouble();
		System.out.println("Enter no of leave:");
		int no_of_leaves = sc.nextInt();
			
		PermanentEmp empOne = new PermanentEmp(empId,empName,total_leaves,paid_leave,sick_leave,casual_leave,basic);
		System.out.println("permanant empdetails");
		System.out.println("EmpId:"+empId);
		System.out.println("Empname:"+empName);
		empOne.calculate_balance_leaves();
		empOne.avail_leave(no_of_leaves, 'P');
		empOne.calculate_salary();
		
	}

}
	


	
