# GUI
综合性实验  学生选课系统设计
---------
一、实验目的
##
1.分析学生选课系统  
2.使用GUI窗体及其组件设计窗体界面  
3.完成学生选课过程业务逻辑编程  
4.基于文件保存并读取数据  
5.处理异常    

二、实验要求
##
一、系统角色分析及类设计  
例如：学校有“人员”，分为“教师”和“学生”，教师教授“课程”，学生选择课程。
定义每种角色人员的属性，及其操作方法。
属性示例：	人员（编号、姓名、性别……）  
教师（编号、姓名、性别、所授课程、……）  
			学生（编号、姓名、性别、所选课程、……）  
二、要求:  
1.设计GUI窗体，支持学生注册、课程新加、学生选课、学生退课、打印学生选课列表等操作。  
2.基于事件模型对业务逻辑编程，实现在界面上支持上述操作。  
3.针对操作过程中可能会出现的各种异常，做异常处理。  
4.基于输入/输出编程，支持学生、课程、教师等数据的读写操作。  
三、核心代码
##
    //注册
     public static void main(String[] args) {
        new SignUp();
    }


    //事件监听
    class DataFind implements ActionListener{
        public void actionPerformed(ActionEvent e) {
            String str0 = jtf.getText();
            String str1 = jta.getText();
            boolean find = false;
            FileWriter fw = null;
            String ss="";
            try {
                Scanner sc = new Scanner(new File("123.txt"));
                while(sc.hasNextLine()) {
                    ss = sc.nextLine();
                    String[] strings = ss.split(" ");
                    if(strings[0].equals(str0)) {
                        find = true;
                        break;
                    }

                }
                if(find)
                    JOptionPane.showMessageDialog(null,"账号已存在");
                else{
                    JOptionPane.showMessageDialog(null,"注册成功");
                    String store = str0 + " " + str1;
                    File file = new File("123.txt");
                    fw = new FileWriter(file, true);
                    fw.write("\n");
                    fw.write(store);
                    fw.close();
                }

            } catch (Exception e2) {
                // TODO: handle exception
            }
            
     //登录
            public static void main(String[] args) {

        new Login();
    }


    //事件监听
    class DataFind implements ActionListener{
        public void actionPerformed(ActionEvent e) {
            String str0 = jtf.getText();
            String str1 = jta.getText();
            boolean find = false;
            String ss="";
            try {
                Scanner sc = new Scanner(new File("123.txt"));
                while(sc.hasNextLine()) {
                    ss = sc.nextLine();
                    String[] strings = ss.split(" ");
                    if(strings[0].equals(str0)&&strings[1].equals(str1)) {
                        find = true;
                        break;
                    }

                }
                if(find){
                    JOptionPane.showMessageDialog(null,"验证通过！");
                Course cour = new Course();
				cour.setVisible(true);
				dispose();
                }
                else
                    JOptionPane.showMessageDialog(null,"验证没有通过！");

            } catch (Exception e2) {
                // TODO: handle exception
            }
            
     //选课
         public static void main(String[] args) {

        new Course();
    }


    //事件监听
    class DataFind implements ActionListener{
        public void actionPerformed(ActionEvent e) {
      //            String str0 = jtf.getText();
      //            String str1 = jta.getText();
            String xinxi = jti.getText();  // 选课信息
            boolean find = false;
            FileWriter fw = null;
            String ss="";
            StringBuilder info=new StringBuilder();
            String name=jtf.getText();
            String num=jta.getText();
            String sex;
            if(rb1.isSelected()){
                sex="男";
            }else {
                sex="女";
            }
            info.append(name+num+sex);
            if(cb1.isSelected()){
                String c=cb1.getText();
                String t=t1.getSelectedItem().toString();
                info.append(":"+c+"-"+t);
            }
            if(cb2.isSelected()){
                String c=cb2.getText();
                String t=t2.getSelectedItem().toString();
                info.append(","+c+"-"+t);
            }
            if(cb3.isSelected()){
                String c=cb3.getText();
                String t=t3.getSelectedItem().toString();
                info.append(","+c+"-"+t);
            }
            jti.setText(info.toString());                     // 把学生信息和选课信息放到文本框中               
        
            //选课信息录入123文本
            try {
                Scanner sc = new Scanner(new File("123.txt"));
                while(sc.hasNextLine()) {
                    ss = sc.nextLine();
                    String[] strings = ss.split(" ");
                    if(strings[0].equals(xinxi)) {
                        find = true;
                        break;
                    }

                }
                if(find)
                    JOptionPane.showMessageDialog(null,"该课已存在");
                else{
                    JOptionPane.showMessageDialog(null,"添加课成功");
                    String store = xinxi + " " ;
                    File file = new File("123.txt");
                    fw = new FileWriter(file, true);
                    fw.write("\n");
                    fw.write(store);
                    fw.close();
                }

            } catch (Exception e2) {
                // TODO: handle exception
            }
     
     
     
    //人员信息        
            public People() {
    }

    public People(String stuId, String name, String sex) {
        this.stuId = stuId;
        this.name = name;
        this.sex = sex;
    }

    public String getStuId() {
        return stuId;
    }

    public void setStuId(String stuId) {
        this.stuId = stuId;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSex() {
        return sex;
    }

    public void setSex(String sex) {
        this.sex = sex;
    }
    }
    
四、运行截图
##

![Image text]
![Image text] 
![Image text] 
![Image text] 

五、说明
##
学生选课系统，可以进行账号注册，并将账号信息存在txt中，利用注册的账号进行登录选课，登录验证等，选课信息同样存在txt中，可以进行修改。更新txt即可。  
六、编程感想
##
这次编程花费时间比较久，特别是信息的存储，还有就是信息的时候，比如你注册的时候，写入的姓名，学号，密码，三个信息，存的时候吧他全部存进去，然后取的时候，要取姓名和密码，不知道怎么实现，取的时候只能一通取出来，还有就是io流存放信息，容易出现乱码，在编写的时候要注意统一。
