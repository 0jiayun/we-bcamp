# jdbc
## 1.加载驱动 
#### 1)右击项目 -> Build Path -> Configure Build Path -> Add Exteranl JARs...

#### 2)q驱动名：com.mysql.jdbc.Driver

 >加载方式：Class.forName(com.mysql.jdbc.Driver)
 
 ## 2.数据库链接与关闭
 
 #### 1)首先导入包 **import java.sql.***
 
>1其中包含了DriverManager(相当一个管家，获取数据库链接并管理)

>2通过代码

    // 数据库地址

	private static String
	
	dbUrl="jdbc:mysql://localhost:3306/db_book";
	
	// 用户名
	
	private static String dbUserName="root";
	
	// 密码
	
	private static String dbPassword="123456";
	
	// 驱动名称
	
	private static String
	
	jdbcName="com.mysql.jdbc.Driver";


#### 2)获取接口代码：

_Connection con=DriverManager.getConnection(dbUrl, dbUserName, dbPassword);_![image](https://note.youdao.com/favicon.ico)
#### 3)关闭通过con.close()
>一般是在finally中完成
#### ***注意异常处理***(eclipse 中快捷键 ctrl+1)

>例子代码：

>package com.java1234.jdbc.chap02.sec04;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Demo1 {

	// 数据库地址
	private static String dbUrl="jdbc:mysql://localhost:3306/db_book";
	// 用户名
	private static String dbUserName="root";
	// 密码
	private static String dbPassword="123456";
	// 驱动名称
	private static String jdbcName="com.mysql.jdbc.Driver";
			
	public static void main(String[] args) {
		try {
			Class.forName(jdbcName);
			System.out.println("加载驱动成功！");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			System.out.println("加载驱动失败！");
		}
		Connection con=null;
		try {
			// 获取数据库连接
			con=DriverManager.getConnection(dbUrl, dbUserName, dbPassword);
			System.out.println("获取数据库连接成功！");
			System.out.println("进行数据库操作！");
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}finally{
			try {
				con.close();
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}
}


