# xiaohaiwen
读写文件
C++中，读写文件操作记录

[1]ofstream :写文件
[2]ifstream :读文件
[3]fstream :读写文件

一、写文件操作
1、包含头文件
  #include<fstream>
2、创建流对象
  ofstream ofs;
3、打开文件
  ofs.open("文件路径"，打开方式）;
4、写数据
  ofs << "写入的数据";
5、关闭文件
  ofs.close();

打开方式总结：
![image](https://github.com/user-attachments/assets/00a48b54-670b-4db4-8049-814878b9439a)
***注意！！！ 文件打开方式可以配合使用，利用 | 操作符即可

二、读文件操作
1、包含头文件
  #include<fstream>
2、创建流对象
  ifstream ifs;
3、打开文件并判断文件是否打开
  ifs.open("文件路径"，打开方式）;
  判断：
  [ifs.is_open()]:返回值为bool型，打开为真，没打开为假，具体判断如下
  if( !isf.is_open())
  {
    cout << "文件打开失败" << endl;
    return;
  }
4、读数据
  四种方式读取
  [1]  char buf[1024] ={ 0 };  //初始化buf数组
        while ( ifs >> buf )   //当数据全部读到buf里，退出循环
        {
          cout << buf << endl;
        }
  [2]  char buf[1024] ={ 0 };  //初始化buf数组
        while ( ifs.getline ( buf,sizeof(buf) )   //getline为ifstream的成员函数，获取一行
        {                                       //getline(数组名，数组大小)
          cout << buf << endl;
        }
  [3]  string buf;  //注意用这个方法需要包含string头文件
        while ( getline ( ifs,buf )   //当数据全部读到buf里，退出循环
        {
          cout << buf << endl;
        }
  [4]  char c;
        while ( ( c = ifs.get() ) != EOF )   //get每次只读一个字符
        {                                     //EOF end of file 文件尾
          cout << buf << endl;
        }  //一般不推荐使用第四种方式
5、关闭文件
  ifs.close();



