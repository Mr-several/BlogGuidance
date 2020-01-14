# markdown图片显示的bug

因为好像是路径中存在空格或者井号的话markdown的图片显示就会出错，所以在格式上不要使用C# 这种类型的路径，否则不会显示图片
*****
网络上的解答：
VS Code的Markdown渲染基于markdown-it，遵循CommonMark。貌似这个标准不允许路径中出现空格、井号之类的东西。
*****
