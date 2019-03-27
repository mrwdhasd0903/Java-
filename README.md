package chp03;
import java.util.Scanner;

public class Exercise3_06
{
	public static void main(String args[]) 
	{	
		boolean bl=true;
		Scanner in=new Scanner(System.in);
		
		System.out.println("输入行数和列数");
		int n=in.nextInt();
		int m=in.nextInt();
		int a[][]=new int[m][n];
		
		System.out.println("依次输入数组");
		shuru(a);
		
		System.out.println("\n数组为:");
		shuch(a);
		here:
		for(int i=0;i<n;i++)
			for(int j=0;j<m;j++)
			{bl=bl&&xunzhao(a,i,j,n,m);
				if(xunzhao(a,i,j,n,m))
					System.out.println("第"+(i+1)+"行第"+(j+1)+"列的"+a[i][j]+"是马鞍数");
					break here; 
			}
		
		if(!bl)System.out.println("找不到马鞍数");
	} 

	
	static boolean xunzhao(int a[][],int c,int v,int n,int m)
	{
		int ma=a[c][v];
		boolean flag=true;
		for(int i=0;i<n;i++)
			if(ma<a[i][v])
				flag=false;
		
		for(int j=0;j<m;j++)
			if(ma>a[c][j])
				flag=false;
		
		return flag;
	}
	
	static void shuru(int a[][])
	{	
		Scanner in=new Scanner(System.in);
		for(int i=0;i<a.length;i++)
			for(int j=0;j<a[i].length;j++)
				a[i][j]=in.nextInt();
	}

	
	static void shuch(int a[][])
	{
		for(int[] i:a)
		{
			for(int j:i)
			System.out.print(j+"\t");
			System.out.println();
		}
	}
}
