# 图书借阅管理系统启动指南

## 一、项目部署环境准备

1. **安装JDK 1.8**
   - 确保已安装JDK 1.8或更高版本
   - 配置JAVA_HOME环境变量

2. **安装Tomcat 8.x/9.x**
   - 下载地址：https://tomcat.apache.org/
   - 解压到本地目录（如：D:\Tomcat）
   - 配置CATALINA_HOME环境变量

3. **安装MySQL数据库**
   - 安装MySQL 5.7或8.0
   - 设置root用户密码

## 二、数据库配置

1. **创建数据库**

   ```sql
   CREATE DATABASE books DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
   ```

2. **导入数据库脚本**

   - 运行数据库脚本：`02-数据库\books.sql`
   - 可以使用MySQL Workbench或命令行导入
   - 命令行导入：`mysql -u root -p books < 02-数据库\books.sql`

3. **修改数据库连接配置**

   - 打开文件：`src\database.properties`
   - 根据实际情况修改以下配置：

   ```properties
   driver=com.mysql.jdbc.Driver
   url=jdbc:mysql://localhost:3306/books?useUnicode=true&characterEncoding=utf8
   username=root
   password=你的MySQL密码
   ```

## 三、项目部署到Tomcat

使用Eclipse或IDEA部署

1. **在Eclipse中导入项目**
   - 选择：File -> Import -> Existing Projects into Workspace
   - 选择项目路径：`d:\桌面\作业\数据库\图书借阅管理系统\01-源码\books\books`

2. **配置Tomcat服务器**
   - Window -> Show View -> Servers
   - 右键 -> New -> Server -> Apache -> Tomcat v8.x Server
   - 配置Tomcat安装目录

3. **部署项目**
   - 将books项目添加到Tomcat服务器
   - 右键Tomcat服务器 -> Start启动服务器

## 四、启动和访问系统

1. **启动Tomcat服务器**
   - 手动启动：运行`Tomcat安装目录\bin\startup.bat`
   - 或通过IDE启动

2. **访问系统**
   - 打开浏览器，访问：http://localhost:8080/books
   - 默认管理员账号：admin
   - 默认密码：123456（加密后为：4QrcOUm6Wau+VuBX8g+IPg==）

## 五、常见问题解决

1. **数据库连接失败**
   - 检查数据库是否启动
   - 确认database.properties配置正确
   - 检查MySQL驱动JAR包是否在lib目录中

2. **Tomcat启动失败**
   - 检查端口8080是否被占用
   - 查看`Tomcat安装目录\logs\catalina.out`日志

3. **页面访问404错误**
   - 确认项目部署正确
   - 检查URL路径是否正确

## 六、项目结构说明

- **src/com/sxt/utils/**: 工具类目录（包含已实现的BeanUtil等）
- **src/com/sxt/dao/**: 数据访问层
- **src/com/sxt/service/**: 业务逻辑层
- **src/com/sxt/web/servlet/**: Servlet控制器
- **WebContent/**: Web页面和静态资源
  - **admin/**: 管理员页面
  - **user/**: 用户页面
  - **static/**: 静态资源（CSS、JS、图片等）
  - **WEB-INF/**: 配置文件和lib库# library
