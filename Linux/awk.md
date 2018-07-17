# 选项
-F :紧跟分隔符，表示读入的字段以输入的分隔符分割  
-v var=value ：进入变量模式 可以进行变量的赋值及调用（调用不需要加$符）

##### 变量如下:
|变 量|	描述|
|:--:|:--:|
|$n|	当前记录的第n个字段，字段间由FS分隔。|
|$0|	完整的输入记录。|
|NF|	当前记录中的字段数(列数)。
|NR|	当前记录数(行数)。
|OFS|	输出字段分隔符(默认值是一个空格)。
|ORS|	输出记录分隔符(默认值是一个换行符)。
|FS|	输入字段分隔符(默认是任何空格)。
|RS	| 输入记录分隔符(默认是一个换行符)。
|ARGC|	命 令行参数的数目。|
|ARGIND|	命令行中当前文件的位置(从0开始算)。
|ARGV|	包 含命令行参数的数组。
|CONVFMT|	数字转换格式(默认值为%.6g)
|ENVIRON|	环境变量关联数组。
|ERRNO|	最后一个系统错误的描述。
|FIELDWIDTHS| 字段宽度列表(用空格键分隔)。
|FILENAME|	当前文件名。
|FNR| 同NR，但相对于当前文件。
|IGNORECASE|	如果为真，则进行忽略大小写的匹配。
|OFMT|	数字的输出格式(默认值是%.6g)。
|RSTART|	由match函数所匹配的字符串的第一个位置。
|SUBSEP|	数组下标分隔符(默认值是\034)。
|RLENGTH	|由match函数所匹配的字符串的长度。
## eg:
##### cat test
first second third  
1 2 3  
a b c  

#### 输出第一行:
awk  '{print $1}' test  
##### result:  
first
1
a

#### 改变输出格式:
awk -v OFS=: '{print $1,$2,$3}' test  

##### result:
first:second:third  
1:2:3  
a: b:c

#### 输出第一列是数字的行  
awk  '{ if($1 ~ /[0-9]/){print $0;} }' test  
##### result:  
1 2 3