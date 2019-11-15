# Spring 路径

## spring中Classpath路径

clsspath指的是class路径,一般src路径下的文件,用maven构建是,包括resources目录.  
可以使用`System.getProperty("java.class.path")`打印classpath路径信息,使用`System.getProperty("user.dir")`打印当前路径信息.
