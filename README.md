package mama;
import java.util.Scanner;

public class Exercise3_06
{
	public static void main(String args[]) 
	{	
		boolean bl=false;
		Scanner in=new Scanner(System.in);
		
		System.out.println("输入行数和列数");   //确定数组的长度和高度
		int n=in.nextInt();
		int m=in.nextInt();
		int a[][]=new int[m][n];
		
		System.out.println("依次输入数组");		//输入数组
		shuru(a);
		
		System.out.println("\n数组为:");		//输出数组
		shuch(a);
		
		here:								//跳出到这
		for(int i=0;i<n;i++)				//两个for循环遍历二维数组，确定是不是马鞍数
			for(int j=0;j<m;j++)
			{bl=bl||xunzhao(a,i,j,n,m);		//xunzhao函数，马鞍数返回真，当每个数都不是马鞍数时，bl为假
				if(xunzhao(a,i,j,n,m))		//xunzhao函数，马鞍数返回真，四个参数分别为：数组，该数的行坐标，列坐标，数组行数，数组列数
					{
					 System.out.println("第"+(i+1)+"行第"+(j+1)+"列的"+a[i][j]+"是马鞍数");	//若返回真，则输出该数
					 break here;			//跳出
					}
			}
		
		if(!bl)System.out.println("找不到马鞍数");		//确定不是马鞍数,则输出不是
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
