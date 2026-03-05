0、如下代码，输出结果正确的是（D）
def makebold(fn):    
def wrapped():
        return "<b>" + fn() + "</b>"    
return wrapped
def makeitalic(fn):    
def wrapped():
        return "<i>" + fn() + "</i>"    
return wrapped
@makebold
@makeitalic
def hello():    
return "hello"
print(hello())
A: <b> <i>hello</b></i>
B: <b> </b>hello<i></i>
C: <b> </b><i></i>hello
D: <b> <i>hello</i></b>
