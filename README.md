#include<iostream>·
#include <Windows.h>
using namespace std;



class Clock//定义钟表类型
{

private://数据成员为私有成员

	int Hour;
	int Minute;
	int Second;
	float Price;

public://函数成员为公有成员
	void Set(int h,int m,int s, float p);
	void Run();
	void Report_Time();
	void Show_Time(){cout<<Hour<<':'<<Minute<<':'<<Second;};

};

void Clock::Set(int h,int m,int s,float p) //设置修改4个数据成员的值的函数

{
	Hour = h;
	Minute = m;
	Second = s;
	Price = p;
}


void Clock::Run() //模拟钟表运行函数
{
   int i=0;
   for(i=0;i<10;i++)//模拟运行10秒
   {
	   Second++;
	   if(Second==60)
	   {
		   Second=0;
		   Minute++;
           if(Minute==60)
		   {
			   Minute=0;
			   Hour++;
			   if(Hour==24)
			   {
				   Hour=0;
			   }
		   }
	   }
	   cout<<'\r';
	   Show_Time();//不换行，放到首位
       Sleep(1000);//程序暂停运行秒
   }

} 

void Clock::Report_Time()
{

	Show_Time();
		if(Minute==0&&Second)
		{
			for(int i=0;i<Hour;i++)//响铃，报时

			{
				cout<<"\007";
				Sleep(1000);
			
			}
		}
}

int main()
{

	Clock XJTU_Big_Ben;
    XJTU_Big_Ben.Set(0,0,0,1000);
	cout<<"钟表设置的时间：\n";
    
	XJTU_Big_Ben.Report_Time();
	XJTU_Big_Ben.Run();
	system("pause");
	XJTU_Big_Ben.Set(9,59,50,9000);
    cout<<"钟表设置的时间：\n";
	XJTU_Big_Ben.Run();
    cout<<endl;
	XJTU_Big_Ben.Report_Time();
	cout<<endl;
    XJTU_Big_Ben.Show_Time();
    cout<<endl;
	Clock Omiga;
	cout<<"显示Omiga的时间";
    Omiga = XJTU_Big_Ben;
    XJTU_Big_Ben.Show_Time();
    cout<<endl;
	return 0;
}
