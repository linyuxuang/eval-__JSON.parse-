# eval-__JSON.parse-
eval()和JSON.parse()区别


        我们将一个字符串解析成json对象时可以使用两种方法：

          假设我们有一个json格式的字符串：

          '{
              "student" : [
                  {"name":"鸣人","age":17}, 
                  {"name":"小樱","age":17}
              ]
          }'
          
       然后我们需要把它解析成json对象

       1、eval（）代码如下：

        var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":17}]}';
        eval('(' + data + ')');
        
       2、JSON.parse()代码如下：

        var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":17}]}';
        JSON.parse(data);
        
        
       区别：eval方法不会去检查给的字符串时候符合json的格式~
       同时如果给的字符串中存在js代码eval也会一并执行~
       比如如果上面的json格式的字符串改为：{"name":"小樱","age":alert("hehe")}

       var data = '{"student" : [{"name":"鸣人","age":17}, {"name":"小樱","age":alert("hehe")}]}'; 
        
        此时执行eval方法后会先弹出一个提示框输出hehe的字符串
        ~但是使用JSON.parse()就会报错~显示错误信息为当前字符串不符合json格式
        ~即JSON.parse()方法会检查需要转换的字符串是否符合json格式
        ~相比较而言eval方法是很危险的~特别是当涉及到第三方时我们需要确保传给eval的参数是我们可以控制的
        ~不然里面插入比如window.location~指向一个恶意的连接~那叫叫天啦 
        
        
        从这个层面讲~还是推荐使用JSON.parse来实现json格式字符串的解析
        
        
      JSON.stringify()用于从一个对象解析出字符串，如


            var a = {a:1,b:2}

            结果：

             JSON.stringify(a)

             "{"a":1,"b":2}"
        
        
        
        
        
        
        
        
        
        
