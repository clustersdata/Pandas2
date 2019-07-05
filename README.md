# Pandas2
Pandas
Pandas中的关于行列选择的十大技能，这些技能，绝对是你使用Pandas的过程中，需要用到的，因为，你肯定也想像Excel一样，任性地操作Python中的数据框。

                                               



       先来导入演示数据

# 导入pandas模块
import pandas as pd
# 创建一个关于fictional army的dataframe示例
raw_data = {
    'regiment': ['Nighthawks', 'Nighthawks', 'Nighthawks', 'Nighthawks', 'Dragoons',
    'Dragoons', 'Dragoons', 'Dragoons', 'Scouts', 'Scouts', 'Scouts', 'Scouts'],
    'company': ['1st', '1st', '2nd', '2nd', '1st', '1st', '2nd', '2nd','1st', '1st', '2nd', '2nd'],
    'deaths': [523, 52, 25, 616, 43, 234, 523, 62, 62, 73, 37, 35],
    'battles': [5, 42, 2, 2, 4, 7, 8, 3, 4, 7, 8, 9],
    'size': [1045, 957, 1099, 1400, 1592, 1006, 987, 849, 973, 1005, 1099, 1523],
    'veterans': [1, 5, 62, 26, 73, 37, 949, 48, 48, 435, 63, 345],
    'readiness': [1, 2, 3, 3, 2, 1, 2, 3, 2, 1, 2, 3],
    'armored': [1, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 1],
    'deserters': [4, 24, 31, 2, 3, 4, 24, 31, 2, 3, 2, 3],
    'origin': ['Arizona', 'California', 'Texas', 'Florida', 'Maine', 'Iowa', 'Alaska', 'Washington', 'Oregon', 'Wyoming', 'Louisana', 'Georgia']
}
 
df = pd.DataFrame(
    raw_data, 
    columns = ['origin','regiment', 'company', 'deaths', 'battles', 'size', 'veterans', 'readiness', 'armored', 'deserters']
)
 
df = df.set_index('origin')
 
df.head()
 

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
California	Nighthawks	1st	52	42	957	5	2	0	24
Texas	Nighthawks	2nd	25	2	1099	62	3	1	31
Florida	Nighthawks	2nd	616	2	1400	26	3	1	2
Maine	Dragoons	1st	43	4	1592	73	2	0	3
Iowa	Dragoons	1st	234	7	1006	37	1	1	4
Alaska	Dragoons	2nd	523	8	987	949	2	0	24
Washington	Dragoons	2nd	62	3	849	48	3	1	31
Oregon	Scouts	1st	62	4	973	48	2	0	2
Wyoming	Scouts	1st	73	7	1005	435	1	0	3
Louisana	Scouts	2nd	37	8	1099	63	2	1	2
Georgia	Scouts	2nd	35	9	1523	345	3	1	3
1、选择一列

df['size']
    输出结果

origin
Arizona       1045
California     957
Texas         1099
Florida       1400
Maine         1592
Iowa          1006
Alaska         987
Washington     849
Oregon         973
Wyoming       1005
Louisana      1099
Georgia       1523
Name: size, dtype: int64
2、选择多列

df[['size', 'veterans']]
    输出结果

origin	size	veterans
Arizona	1045	1
California	957	5
Texas	1099	62
Florida	1400	26
Maine	1592	73
Iowa	1006	37
Alaska	987	949
Washington	849	48
Oregon	973	48
Wyoming	1005	435
Louisana	1099	63
Georgia	1523	345
3、根据一个行索引，选择出一行

# 选择索引标签为“Arizona”的所有行
df.loc[:'Arizona']
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
4、根据一个行序号，选择出从开始到这个序号的行

# 选择每一列的2行数据
df.iloc[:2]
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
California	Nighthawks	1st	52	42	957	5	2	0	24
5、根据两个行序号，选择出从第一个序号到第二个序号的行

df.iloc[1:2]
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
California	Nighthawks	1st	52	42	957	5	2	0	24
6、根据一个行序号，选择出从这个行序号开始到结束的行

df.iloc[2:]
    输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Texas	Nighthawks	2nd	25	2	1099	62	3	1	31
Florida	Nighthawks	2nd	616	2	1400	26	3	1	2
Maine	Dragoons	1st	43	4	1592	73	2	0	3
Iowa	Dragoons	1st	234	7	1006	37	1	1	4
Alaska	Dragoons	2nd	523	8	987	949	2	0	24
Washington	Dragoons	2nd	62	3	849	48	3	1	31
Oregon	Scouts	1st	62	4	973	48	2	0	2
Wyoming	Scouts	1st	73	7	1005	435	1	0	3
Louisana	Scouts	2nd	37	8	1099	63	2	1	2
Georgia	Scouts	2nd	35	9	1523	345	3	1	3
7、根据一个列序号，选择出从开始列到这个序号的所有列

# 选择前三列
df.iloc[:,:3]
   输出结果

origin	regiment	company
Arizona	Nighthawks	1st
California	Nighthawks	1st
Texas	Nighthawks	2nd
Florida	Nighthawks	2nd
Maine	Dragoons	1st
Iowa	Dragoons	1st
Alaska	Dragoons	2nd
Washington	Dragoons	2nd
Oregon	Scouts	1st
Wyoming	Scouts	1st
Louisana	Scouts	2nd
Georgia	Scouts	2nd
8、条件过滤

   1.选择死亡人数大于50的行

# 选择df.deaths大于50的行
df[df['deaths'] > 50]
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
California	Nighthawks	1st	52	42	957	5	2	0	24
Florida	Nighthawks	2nd	616	2	1400	26	3	1	2
Iowa	Dragoons	1st	234	7	1006	37	1	1	4
Alaska	Dragoons	2nd	523	8	987	949	2	0	24
Washington	Dragoons	2nd	62	3	849	48	3	1	31
Oregon	Scouts	1st	62	4	973	48	2	0	2
Wyoming	Scouts	1st	73	7	1005	435	1	0	3
   2.选择死亡人数大于500或小于50的行

# 选择df.death大于500或小于50的行
df[(df['deaths'] > 500) | (df['deaths'] < 50)]
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
Texas	Nighthawks	2nd	25	2	1099	62	3	1	31
Florida	Nighthawks	2nd	616	2	1400	26	3	1	2
Maine	Dragoons	1st	43	4	1592	73	2	0	3
Alaska	Dragoons	2nd	523	8	987	949	2	0	24
Louisana	Scouts	2nd	37	8	1099	63	2	1	2
Georgia	Scouts	2nd	35	9	1523	345	3	1	3
   3.选择所有没有命名为"龙骑兵"的兵团

# 选择所有没有命名为"Dragoons"的兵团
df[~(df['regiment'] == 'Dragoons')]
   输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
California	Nighthawks	1st	52	42	957	5	2	0	24
Texas	Nighthawks	2nd	25	2	1099	62	3	1	31
Florida	Nighthawks	2nd	616	2	1400	26	3	1	2
Oregon	Scouts	1st	62	4	973	48	2	0	2
Wyoming	Scouts	1st	73	7	1005	435	1	0	3
Louisana	Scouts	2nd	37	8	1099	63	2	1	2
Georgia	Scouts	2nd	35	9	1523	345	3	1	3
9、根据行字符串索引，进行行选择

# 选择称为Texas和Arizon的行
df.ix[['Arizona', 'Texas']]
    输出结果

origin	regiment	company	deaths	battles	size	veterans	readiness	armored	deserters
Arizona	Nighthawks	1st	523	5	1045	1	1	1	4
Texas	Nighthawks	2nd	25	2	1099	62	3	1	31
10、根据行索引/行位置，列名/列位置，进行具体位置的值选择

# 选择行中名为Arizona的第三个单元格
df.ix['Arizona', 'deaths']
523
# 选择行中名为Arizona的第三个单元格
df.ix['Arizona', 2]
523
# 在“deaths”列中选择第三个单元格
df.ix[2, 'deaths']
25
