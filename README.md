# test_5_2
#include <stdio.h>
#include <stdlib.h>
//串的顺序存储
//静态数组
#define MAXLEN 255
typedef struct{
	char ch[MAXLEN];
	int length;
}SString;
//堆分配存储（动态存储）
typedef struct{
	char *ch;
	int length;
}HString;
//链式存储
typedef struct StringNode{
	char ch;//每个结点存储1个字符
	struct StringNode* next;
}StringNode,*String;
typedef struct StringNode{
	char ch[4];//每个结点存储4个字符
	struct StringNode* next;
}StringNode,*String;
//基本操作
//求子串(静态数组）
bool SubString(SString &Sub,SString S,int pos,int len)
{
	if(pos+len-1>S.length)//判断子串是否出界
		return false;
	for(int i=pos;i<pos+len;i++)
		Sub.ch[i-pos+1] = S.ch[i];
	Sub.length = len;
	return true;
}
//比较串
int Strcompare(SString S,SString T)
{
	for(int i =1;i<S.length && i<T.length;i++)
	{
		if(S.ch[i] != T.ch[i])
			return S.ch[i] - T.ch[i];
	}
	return S.length - T.length;
}
//子串在主串中的位置
int Index(SString S,SString T)
{
	int i = 1,n=Strlength(S),m=Strlength(T);
	SString Sub;
	while(i<=n-m+1)
	{
		SubString(Sub,S,i,m);
		if(Strcompare(Sub,T) != 0)
			++i;
		else
			return i;
	}
	return 0;
}
int main()
{
	SString S;
	SString T;
	HString S;
	S.ch=(char*)malloc(sizeof(char)*MAXLEN);
	S.length = 0;
	Strlength(S);
	SubString(&Sub,S,pos,len);
	Strcompare(S,T);
	Index(S,T);
	ClearString(&S);
	DestoryString(&S);
	Concat(&T,S1,S2);
	StrEmpty(S);
	Strcpy(&T,S);
	StrAssign(&T,chars);
	return 0;
}
