# 9.12.1-
全局寿命，局部可见
// 9.12静态生存期.cpp : 定义控制台应用程序的入口点。
//

#include "stdafx.h"
#include <iostream>

using namespace std;

int i=1;
void other()
{
	static int a=2;
	static int b;
	//a,b为静态局部变量，具有全局寿命，局部可见。
	//只在第一次进入函数时被初始化。
	int c=10;
	//c为局部变量，具有动态生存期。
	//每次进入函数时都初始化。
	a+=2; c+=5;i+=32;
	cout<<"other\n"<<"i="<<i<<" a="<<a<<" b:"<<b<<" c:"<<c<<endl;
	b=a;
}
int _tmain(int argc, _TCHAR* argv[])
{
	static int a;
	int b=-10; // b,c为局部变量，具有动态生存期。
	int c=0;
	cout<<"main\n"<<"i="<<i<<" a="<<a<<" b:"<<b<<" c:"<<c<<endl;
	c+=8;
	other();
	i+=10;
	other();
	cout<<"main\n"<<"i="<<i<<" a="<<a<<" b:"<<b<<" c:"<<c<<endl;
	return 0;
}

main
i=1 a=0 b:-10 c:0
other
i=33 a=4 b:0 c:15
other 
i=75 a=6 b=4 c:15
main
i=75 a=0 b:10 c:8
