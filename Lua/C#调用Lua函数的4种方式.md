1、泛型调用

lua代码
```
test={}
function test.luaFunc(num)
    return num+1
end
```
C#代码
```
LuaFunc luaFunc=null;
DelegateFactory.Init();
luaFunc =lua.GetFunction("test.luaFunc");
```
```
int num=luaFunc.Invoke<int,int>(12345);
```
2、委托调用
```
Func<int,int> func=luaFunc.ToDelegate<Func<int,int>>();
int num=func(12345);
```
3、扩展调用
```
//开始函数调用
luaFunc.BeginPCall();
//参数入栈
luaFunc.Push(12345);
//调用函数
luaFunc.PCall();
//获取结果
int num=(int)luaFunc.CheckNumber();
//结束调用
luaFunc.EndPCall();
```
4、LuaState调用
```
lua.Invoke<int,int>("test.luaFunc",12345,true);
```