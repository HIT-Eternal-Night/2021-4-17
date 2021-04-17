# 2021-4-17
继续指针和字符串练习

1、
利用指针能直接操作内存的特点来编程输出字符串中每个字符在内存中的存储编码（字符串中可以包含英文数字和汉字）。
程序的运行示例1如下：
请输入一个字符串，长度小于等于100：abcABC012中国人
该字符串的内存编码为： 61 62 63 41 42 43 30 31 32 d6 d0 b9 fa c8 cb 
程序的运行示例2如下：
请输入一个字符串，长度小于等于100：12345上山打老虎
该字符串的内存编码为： 31 32 33 34 35 c9 cf c9 bd b4 f2 c0 cf bb a2
提示：
输出格式用"%x "
提示：为了不输出多余的ffff，
请用printf("%x ", (unsigned char)str[i] & 0xff);
或者
if (str[i] > 0xffffff00) printf("%x ", str[i] -0xffffff00);

我的答案：
#include <stdio.h>
#include <string.h>

int main(int argc,char const *argv[])
{
	char str[100];
	char *t = str;
	printf("请输入一个字符串，长度小于等于100："); 
	scanf("%s",str);
	int len = strlen(str);
	int i;
	printf("该字符串的内存编码为： ");
	for (i=0 ; str[i]!='\0' ;i++)
	{
		printf("%x ", (unsigned char)str[i] & 0xff);
	}
	return 0;
}

2、
程序改错。
以下程序的功能是统计字符数。判断一个由’0’ ~ ‘9’这10个字符组成的字符串中哪个字符出现的次数最多。
输入数据：第一行是测试数据的组数m，每组测试数据占1行，每行数据不超过1000个字符且非空。
输出要求：m行，每行对应一组输入，包括出现次数最多的字符和该字符出现的次数。如果有多个字符出现的次数相同且最多，那么输出ASCII码最小的那一个。
#include <stdio.h>
#include <string.h>
main( )
{
int  cases, sum[10], i, max;
  char str[1000];                          
    scanf("%d", case);                    
  while (cases > 0)
       {
                scanf("%c", str);
            for( i = 0; i < 10; i++)
                 sum[i] = 0; 
                    for(i < 0; i < strlen(str); i++)
                ++sum[str[i] – 0];
            max = 0;   
            for (i = 1; i < 10; i++)
                if(sum[i] >＝ sum[max]) max = i;
            printf("%c %d\n", max + '0', sum[0]);
            cases --;
       }
}

我的答案：
#include <stdio.h>
#include <string.h>

int main(int argc,char const *argv[])
{
	int  cases, sum[10], i, max;
	char str[1000];                          
    scanf("%d", &cases);                    
	while (cases > 0)
       {
            scanf("%s", str);
            for( i = 0; i < 10; i++ )		//对sum数组全部初始化为0 
                sum[i] = 0; 
            
			for( i = 0; i < strlen(str); i++ )
                ++sum[str[i]-'0'];			//本题的关键所在：str[i]是一个字符，不能作为sum的下标使用 
            //for( i = 0; i < 10; i++ )    	
            //    printf("sum[%d] = %d\n",i,sum[i]);
            
			max = 0;
            for (i = 1; i < 10; i++)
                if(sum[i] > sum[max]) max = i;//大于而不是大于等于可以保证输出ASCII码最小的数 
            
			printf("%c %d\n", max + '0', sum[max]);
            cases--;
       }
    return 0; 
}
总结：都在注释里了
