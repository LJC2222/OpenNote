__index元方法
    当访问表中一个不存在的字段时，解释器会去该表的原表中查找一个叫__index的元方法。
    
__newindex原方法
    对表中一个不存在的字段赋值时，解释器会去该表的原表中查找一个叫__newindex的原方法。
    
可以赋值为function，也可以赋值为table。
```
function new(o)
    setmetatable(o,mt)
    return o
end
```
```
local o=new{} --应该等价于local o=new({})