# wenjian
课程作业

项目描述：
本项目是用于统计一个导入的纯英文txt文本中的字符数，单词数，句子数，和行数的一个程序。


相关用法：
把所需要统计的txt文件的路径输入到代码中的fopen指令中，点击运行即可实现统计功能。

程序最终代码：能够记录txt文本中的字符数，单词数，行数。
#include <stdio.h>
int main()
{
    int letter=0;//定义字母 
    int digit=0;//定义数字 
    int other=0;//其他字符 
    int word=0;//单词 
	int line=0;//行 
	char c;
	int i;

    FILE * wc ;
    wc = fopen("C:\\Users\\DELL\\Desktop\\文本.txt","r");//打开文本所在的文件夹 
    printf("文本的内容为：\n");
    if (wc != NULL){
    do{
        c = fgetc(wc);
        
		printf("%c",c);
          if((c == '\n' || c == '\t' || c == EOF))
 	     { 
     	     line++;//统计行数	
     	 }
		else if ((c>='a'&&c<='z')||(c>='A'&&c<='Z')){
                    letter++;//统计字母个数 
        }else if (c >= '0' && c <= '9'){
                    digit++;//统计数字个数 
        }
         else if(c==' '||c=='\n'||c=='\t'||c==','||c=='.'||c=='!'||c=='='||c==';')
        {
        
            word++;//统计单词个数 
        }	
        
 	     else {
                    other++;//统计其他字符的个数 
                }
            
			} while (c != feof(wc) && c != EOF);
        fclose(wc);
    }
    
    printf("\n字母的字符数为：%d\n",letter); 
    printf("数字的字符数为：%d\n",digit);
    printf("其他的字符数为：%d\n",other);
    printf("单词数为：%d\n",word); 
    printf("行数为：%d\n",line);
	return 0;
}
