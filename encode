# -*- coding: utf-8 -*-
"""
Created on Wed Apr 18 16:27:07 2018

@author: 65680
"""

def get_input():                             #获得输入
    code=input("your input:")
    
    return code 
def one(code):                               #检验数据中‘1’的个数
    j=0    
    for i in range(0,len(code)):
        if code[i]=='1':
            j=j+1

    return j
#----------------------图元库模块部分----------------------------#    
#---------------------反向不归零编码-----------------------------#    
def NRZ_code():                              #NRZ编码库，前面的数字是这一位，后面的数字是下一位
                                             #01，00，11，10的顺序是为了配合后面的哈希函数
    NRZ_state0_1=[]                          #这一位是0下一位是1，
    NRZ_state0_0=[]                          #规则同上
    NRZ_state1_1=[]                          #
    NRZ_state1_0=[]                          #

    for l in range(0,9):                     #一个图元用7*10的二元列表储存(7这里代表字符串元素个数，后面不做特殊声明)
        NRZ_state0_1.append(["0,0,0,0,0,0,1"])    
    NRZ_state0_1.append(["1,1,1,1,1,1,1"])  

    for k in range(0,9):
        NRZ_state0_0.append(["0,0,0,0,0,0,0"])    
    NRZ_state0_0.append(["1,1,1,1,1,1,1"])

    NRZ_state1_1.append(["1,1,1,1,1,1,1"])
    for j in range(1,10):
        NRZ_state1_1.append(["0,0,0,0,0,0,0"])
        
    NRZ_state1_0.append(["1,1,1,1,1,1,1"])
    for i in range(1,10):
        NRZ_state1_0.append(["0,0,0,0,0,0,1"])
    
    return NRZ_state0_1, NRZ_state0_0,NRZ_state1_1,NRZ_state1_0 #把4个列表作为一个元组返回
#------------------------曼彻斯特编码---------------------------#
def MC_code():                                #MC编码库，前面的数字是这一位，后面的数字是下一位
    MC_state0_1=[]  
    MC_state0_0=[]
    MC_state1_1=[]
    MC_state1_0=[]                            #此顺序也为了配合哈希函数

    MC_state0_1.append(["0,0,0,1,1,1,1"])
    for l in range(1,9):
        MC_state0_1.append(["0,0,0,1,0,0,0"])    
    MC_state0_1.append(["1,1,1,1,0,0,0"])  

    MC_state0_0.append(["0,0,0,1,1,1,1"])
    for k in range(1,9):
        MC_state0_0.append(["0,0,0,1,0,0,1"])    
    MC_state0_0.append(["1,1,1,1,0,0,1"])

    MC_state1_1.append(["1,1,1,1,0,0,1"])
    for j in range(1,9):
        MC_state1_1.append(["0,0,0,1,0,0,1"])
    MC_state1_1.append(["0,0,0,1,1,1,1"])
    
    MC_state1_0.append(["1,1,1,1,0,0,0"])          
    for i in range(1,9):
        MC_state1_0.append(["0,0,0,1,0,0,0"])
    MC_state1_0.append(["0,0,0,1,1,1,1"])

    return MC_state0_1, MC_state0_0,MC_state1_1,MC_state1_0 #把4个列表作为一个元组返回
#--------------------------差动双向编码----------------------------#
def DBP_code():                             #DBP编码库，前面的数字是前一位的电平，后面的数字是这一位的值。
    DBP_statelow_1=[]
    DBP_statelow_0=[] 
    DBP_statehigh_1=[]
    DBP_statehigh_0=[]                      #此顺序也为了配合哈希函数
   
    DBP_statelow_1.append(["1,1,1,1,1,1,1"])
    for i in range(1,10):
        DBP_statelow_1.append(["0,0,0,0,0,0,1"])

    DBP_statelow_0.append(["1,1,1,1,0,0,1"])    
    for l in range(1,9):
        DBP_statelow_0.append(["0,0,0,1,0,0,1"])    
    DBP_statelow_0.append(["0,0,0,1,1,1,1"])  

    for j in range(0,9):
        DBP_statehigh_1.append(["0,0,0,0,0,0,1"])
    DBP_statehigh_1.append(["1,1,1,1,1,1,1"])
    
    DBP_statehigh_0.append(["0,0,0,1,1,1,1"]) 
    for k in range(1,9):
        DBP_statehigh_0.append(["0,0,0,1,0,0,1"])    
    DBP_statehigh_0.append(["1,1,1,1,0,0,1"])
    
    return DBP_statelow_1, DBP_statelow_0,DBP_statehigh_1,DBP_statehigh_0 #把4个列表作为一个元组返回
#----------------------------PIE编码-----------------------------------#
def PIE_code():                             #PIE编码库
    SOF=[]                                  
    EOF=[]
    ZERO=[]
    ONE=[]
    
    SOF.append(["1,0,0,1,1,1,1"])          #SOF4个周期，所以是'7'*40
    for i in range(1,9):
        SOF.append(["1,0,0,1,0,0,1"])
    SOF.append(["1,1,1,1,0,0,1"])
    
    SOF.append(["0,0,0,1,1,1,1"])
    for i in range(1,9):
        SOF.append(["0,0,0,1,0,0,0"])
    SOF.append(["1,1,1,1,0,0,0"])
    
    SOF.append(["1,1,1,1,1,1,1"])
    for i in range(1,10):
        SOF.append(["0,0,0,0,0,0,0"])
        
    SOF.append(["1,1,1,1,1,1,1"])
    for i in range(1,10):
        SOF.append(["0,0,0,0,0,0,1"])
    
    EOF.append(["0,0,0,1,1,1,1"])         #EOF4个周期，也是'7'*40
    for k in range(1,9):
        EOF.append(["0,0,0,1,0,0,0"])
    EOF.append(["1,1,1,1,0,0,0"])
    
    EOF.append(["1,1,1,1,1,1,1"])
    for k in range(1,10):
        EOF.append(["0,0,0,0,0,0,0"])  
    EOF.append(["1,1,1,1,1,1,1"])
    for k in range(1,10):
        EOF.append(["0,0,0,0,0,0,0"])     
    EOF.append(["1,1,1,1,1,1,1"])
    for k in range(1,10):
        EOF.append(["0,0,0,0,0,0,0"]) 
    
    ONE.append(["0,0,0,1,1,1,1"])          #'1'两个周期，所以是'7'*20
    for l in range(1,9):
        ONE.append(["0,0,0,1,0,0,0"])
    ONE.append(["1,1,1,1,0,0,0"])
    ONE.append(["1,1,1,1,1,1,1"])
    for l in range(1,10):
        ONE.append(["0,0,0,0,0,0,1"])     
    
    ZERO.append(["0,0,0,1,1,1,1"])         #'0'一个周期，所以是'7'*10
    for h in range(1,9):
        ZERO.append(["0,0,0,1,0,0,1"])
    ZERO.append(["1,1,1,1,0,0,1"])
    
    return SOF,EOF,ONE,ZERO                 #把4个列表作为一个元组返回
#-----------------------------NRZ,MC,DBP的输出模块-------------------#
#这一部分使用的图元库，是按NRZ(01,00,11,10),MC(01,00,11,10),DBP(l_1,l_0,h_1,h_0)顺序储存#
def output(code,cs,ser,ist):  #code是输入的二进制字符串，cs是这三部分图元库，ser是编码方式选择，ist是前一位电平
    n=len(code)                            #记录字符串长度                     
    con=ist                                #将第1位前的初始电平保存
    buff=[]                                #输出缓存
    for j in range(0,10):                  #逐行
        ist=con                            #写完一行后，将最初的电平给ist（在DBP编码用到）
        for i in range(0,n):               
            if (i+1)==n:                   #是否写到最后一个数(最后一位在图形上要特殊处理)
                m=int(code[i])             #m记录当前位的整型值
                if ser==0:                 #ser=0为NRZ编码 
                    buff.append(cs[4*ser+m+1][j])#使用NRZ(00)或NRZ(11),取决于m
                elif ser==1:               #ser=1为MC编码
                    buff.append(cs[4*ser+3*m][j])#使用MC(01)或MC(10)图元
                elif (ser==2 and m==0):    #ser=2为DBP编码
                    buff.append(cs[7-3*ist][j])#通过哈希函数的偏移借用MC库的图元MC(10)/MC(01)
                else:
                    buff.append(cs[2-ist][j]) #借用NRZ的图元NRZ(11)/NRZ(00)
            elif ser<=1:                   #未到末尾的写入
                s=1+2*int(code[i])-int(code[i+1])#此哈希函数用当前位和后一位的值做参数算出偏移
                buff.append(cs[4*ser+s][j])               #01,00,11,10
                buff.append([','])
            else:
                m=int(code[i])
                s=1+2*ist-m                 #此哈希函数用当前位和前一位的电平做参数算出偏移
                buff.append(cs[4*ser+s][j])#l_0,L_1,H_1,H_0
                ist=abs(ist-m)              #根据DBP'1'改变ist，'0'不改变ist得出
                buff.append([','])
                         
        buff.append('\n')                   #写完一行有换行符
    return buff   
#-----------------------------PIE输出模块--------------------------#
#code为输入的字符串，cs1为PIE图元库，储存顺序为SOF,EOF,'1','0'------#                       
def output_pie(code,cs1):                   #
    n=len(code)
    buffp=[]   
    for j in range(0,10):
        buffp.append(cs1[0][j])             #写一行时先将SOF写入
        buffp.append([','])
        buffp.append(cs1[0][j+10])
        buffp.append([','])            
        buffp.append(cs1[0][j+20])
        buffp.append([','])
        buffp.append(cs1[0][j+30])
        buffp.append([','])    
        for i in range(0,n):
            m=int(code[i])
            if m==0:
                buffp.append(cs1[3][j])   #写'0'的图元
                buffp.append([','])
            else:
                buffp.append(cs1[2][j])   #写'1'的图元
                buffp.append([','])
                buffp.append(cs1[2][10+j])
                buffp.append([','])
        buffp.append(cs1[1][j])          #写一行末尾将EOF写入
        buffp.append([','])
        buffp.append(cs1[1][j+10])
        buffp.append([','])            
        buffp.append(cs1[1][j+20])
        buffp.append([','])
        buffp.append(cs1[1][j+30])
        buffp.append(['\n'])      
    return buffp
#---------------------主函数部分-----------------------#
code=get_input()                #输入值
n=str(7*len(code))              #n作为PPM定义的行的大小（NRZ,MC,DBP）
ll=MC_code()
gg=NRZ_code()
ff=DBP_code()  
cs=gg+ll+ff                     #cs为NRZ,MC,DBP的总图元库
#-----------------NRZ写文件-----------------#
f0=open(r'C:\Users\65680\Desktop\NRZ.PPM','w')
nrz=output(code,cs,0,0)
f0.write('P1\n')
f0.write(n)
f0.write(" 10\n")
for i in range(0,len(nrz)):
    for j in nrz[i]:
        f0.write(j)       
f0.close()
#------------------MC写文件------------------#
f1=open(r'C:\Users\65680\Desktop\MC.PPM','w')
mc=output(code,cs,1,0)
f1.write('P1\n')
f1.write(n)
f1.write(" 10\n")
for i in range(0,len(mc)):
    for j in mc[i]:
        f1.write(j)       
f1.close()
#----------------------DBP写文件--------------#
f2=open(r'C:\Users\65680\Desktop\DBP.PPM','w')
dbp=output(code,cs,2,0)
f2.write('P1\n')
f2.write(n)
f2.write(" 10\n")
for i in range(0,len(dbp)):
    for j in dbp[i]:
        f2.write(j)       
f2.close()
#-----------------------PIE写文件---------------#
k=one(code)                            #二进制数据中1的个数
n1=str(7*len(code)+7*k+56)             #PPM行的宽度(PIE)
hh=PIE_code()                          #PIE的图元库 
f3=open(r'C:\Users\65680\Desktop\PIE.PPM','w')
pie=output_pie(code,hh)                #得到pie的输出缓冲
f3.write('P1\n')
f3.write(n1)
f3.write(" 10\n")
for i in range(0,len(pie)):
    for j in pie[i]:
        f3.write(j)       
f3.close()

