＃ 字节码文件格式
 
 1.可以把字节码文件看层一个结构体，如下：
 
     ClassFile {

      u4 magic; //魔数

      u2 minor_version; //次版本号

      u2 major_version;//主版本号

      u2 constant_pool_count;//常量池大小

      cp_info constant_pool[constant_pool_count-1];// 常量池信息

      u2 access_flags;//类的权限

      u2 this_class;//类型信息

      u2 super_class;//父类信息

      u2 interfaces_count;//接口信息

      u2 interfaces[interfaces_count];//接口个数

      u2 fields_count;//变量个数（包含静态变量，但不包含从父类继承的）

      field_info fields[fields_count];//变量信息

      u2 methods_count;//方法个数（包含静态方法，但不包含从父类继承的）

      method_info methods[methods_count];//方法信息

      u2 attributes_count;//类的属性集合个数

      attribute_info attributes[attributes_count];//属性信息

    }
    
    2.该结构体描述了类文件的所有信息。
    
    3.常量池中存放有类文件中的所有常量，每个常量有自己的索引值，类似public static 信息存储类／方法／接口／变量的access_flag中，没有常量字段
    
    4.常量池后面的类信息／父类信息／接口信息／字段信息／方法信息／属性信息 所涉及的名称，类型等信息都指向常量池中的索引，该索引值会在类的解析阶段，解析成直接引用，因为类加载到内存后，常量池中的所有常量就有个内存地址，解析成直接引用，才可以在jvm中使用
    
    5.类信息／字段信息／方法信息 它们都有属性集合，描述了它们的特点，如code属性，constVaule属性等


