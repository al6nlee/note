[toc]

## 函数基础
```python
# 函数定义
	函数类似于工具，提前定义好就可以反复使用

# 语法结构
	def 函数名(参数1, 参数2...):
	    """函数注释"""
	    函数体代码
	    return 返回值

	"""
	def
		定义函数的关键字
	函数名
		函数的名字  相当于变量名
		函数名的命名规范与风格参考变量名来
	参数
		参数可以没有，也可以为多个
		表示使用函数前需要满足的条件
	函数注释
		类似于产品说明书
		主要用于介绍函数功能 参数使用等
	函数体代码
		函数核心的代码逻辑(重要)
	返回值
		使用函数之后反馈给使用者的结果
	"""

# 函数的调用
	"""
	函数必须先定义再调用
	函数在定义阶段只检测语法，不执行代码
	函数在调用阶段才会执行函数体代码
	"""
	函数名(参数1, 参数2...)

# 函数的分类
	内置函数
		python解释器自带函数
	自定义函数
		"""程序员自己写的函数"""
		无参函数
		有参函数
		空函数 ===》 占位用的

# 函数参数
	形式参数
		在函数定义阶段，括号内填写的参数  简称"形参"
	实际参数
		在函数调用阶段，括号内传入的参数  简称"实参"
	"""
	形参与实参的关系
		可以将形参看成变量名  实参看成变量值
			两者在函数调用阶段临时绑定 函数运行结束即断开
	形参与实参的表现形式
		形参 == 变量名
		实参
			直接传入值
			借助于变量间接传入
			其他方法或者函数的返回值
	
	位置参数
		位置参数就是按照从左往右的顺序依次填入的参数
			位置形参
			位置实参
		"""
		1.位置形参与位置实参在函数调用阶段 按照位置一一对应绑定
		2.位置参数再绑定的时候多一个不行，少一个也不行
		"""
	关键字实参
		在函数调用阶段，指名道姓传值给变量名
		"""
		关键字参数必须跟在位置参数后面！！！
		"""
	默认参数(关键字形参)
		函数在定义阶段就给函数赋值了
			1.该形参在函数调用阶段 如果不给值 则使用默认的
			2.该形参在函数调用阶段也可以传值 传值就会使用传的
		"""
		如果默认参数绑定了一个可变类型参数，需要注意啦，变动的是同一个数据  fun(a, b, c=[])
		默认参数是在定义阶段就确定了值，而非调用阶段
		"""
	可变长形参
		"""函数无论传入多少参数都可以正常运行"""
		fun(x, y, *args, a=True, **kwargs)
		"""
		*号在形参中的作用
			用于接受*多余*的位置参数 并组织成元组的形式赋值给*号后面的变量名
		**号在形参中的作用
			用于接受*多余*的关键字参数 并组织成字典的形式赋值给**号后面的变量名
		"""
	*/**在实参中的应用
		a = [11, 22, 33]
		d = {"name": "alan"}
		def fun(*args, **kwargs):
		    pass
		fun(*a, **d)
		"""
		*号在实参中的使用
			会将列表、元组中的元素打散成位置参数的形式一一传值
		**号
			会将字典打散按照关键字参数的形式一一传值
		"""
	命名关键字参数
		def fun(name, *, sex):
		    pass
		"""sex在传入实参的时候必须以关键字参数传值"""

# 返回值
	函数没有return默认返回None
	函数体只有return没有返回值也是返回None
	函数体遇到return，立刻结束函数体
	函数体return后面写什么，就返回什么
	可以返回多个返回值，默认组织成元组，同时也可以用多个变量去解压赋值，*_可以接受不需要的值
```
## 名称空间
```python
# 什么是名称空间
	用于存放变量名与变量值绑定关系的地方

# 名称空间分类（在函数定义阶段查找顺序就已经定义死了！！！）
	内置名称空间
		python解释器提前定义好的
			print()
		随着python解释器启动与关闭而创建和销毁
	全局名称空间
		py文件中顶格编写的代码在运行之后都会存放在全局名称空间
			例外：if、for、while里面定义的
		随py文件的运行与结束而创建和销毁
	局部名称空间
		函数体运行之后产生的都是局部名称空间
		随着函数代码的执行结束而创建和销毁

# 名字的查找顺序
	在查找名字的时候， 先确定自己所在位置
		1. 在局部
			局部 ==》 全局 ==》 内置
		2.在全局
			全局 ==》 内置

# 作用域
	定义
		名称空间作用的范围
	内置名称空间
		程序任何阶段任何位置均可使用
	全局名称空间
		程序任何阶段任何位置均可使用
	局部名称空间
		一般情况下，只在各自的名称空间有效

# global与nonlocal关键字
	局部修改全局
		不可变类型数据
			关键字global x
		可变类型
			直接修改 无需声明
	局部修改局部：内部局部修改外部局部的不可变类型数据
		关键字nonlocal x
```
## 函数进阶
```python
# 函数名用法(函数对象)
	1.函数名当做函数名赋值
	2.函数名当做函数的实参
	3.函数名当做函数的返回值
	4.函数名当做容器类型的元素

# 函数的嵌套调用
	定义
		函数内部调用其他函数
	示例
		四个数中取出最大的数

# 函数的嵌套定义
	定义
		函数体内部定义其他函数
	应用场景
		将复杂的功能全部隐藏起来，暴露一个简单的接口

# 闭包函数
	闭
		定义在函数体内部的函数
	包
		内部函数引用了外部名称空间的名字

	用途
		闭包函数是给函数传参的第二种方式
		一次调用，后面不需要传数据了

# 装饰器*****
	装饰
		给被装饰对象添加额外功能
	器
		工具
	
	装饰器原则
		开放封闭原则
			开放：对扩展开放
			封闭：对修改封闭
	
	装饰器核心思想
		在不改变被装饰对象内部代码和原有调用方式的基础之上添加额外功能
	
	固定模版
		from functools import wraps
		
		func_name(*args, **kwargs):
		    pass
		
		
		def get_func_name(func_name):   # func_name = 函数名
		    @warps(func_name)  # 装饰器修复技术，用来隐瞒help函数查询的结果
		    def get_time(*args,**kwargs):
		    	# 写入被装饰前的代码体
		    	'''代码体'''
		    	# 用get_return 接收被装饰函数的返回值
		    	get_return = func_name(*args,**kwargs)  # 这里的*、**是将args元组、kwargs字典打散传入func_name
		    	# 写入被装饰后的代码体
		    	'''代码体'''
		    	# 返回被装饰函数的返回值
		    	return get_return
		    return get_time
		
		
		func_name = get_func_name(func_name)
		func_name(*args, **kwargs)	此fun_name并不是之前的func_name,而是get_time(*args, **kwargs)

	语法糖
		形式
			@get_func_name
			func_name(*args, **kwargs)
		
		本质
			将语法糖下面的函数名传递给装饰器函数调用，实现狸猫换太子
		
		三层语法糖
		
	有参装饰器
		def outer(source_data):
		    # source_data = 'file'
		    def login_auth(func):
		        def auth(*args,**kwargs):
		            # 2.校验用户名和密码是否正确
		            # 数据的校验方式可以切换多种
		            if source_data == 'file':
		                # 从文件中获取用户数据并比对
		                print('file文件获取')
		            elif source_data == 'MySQL':
		                # 从MySQL数据库中获取数据比对
		                print('MySQL数据库获取')
		            elif source_data == 'postgreSQL':
		                # 从postgreSQL数据库中获取数据对比
		                print('postgreSQL数据库获取')
		            else:
		                print('用户名或密码错误 无法执行函数')
		        return auth
		    return login_auth

		@outer('file')
		def index():
		    print('from index')
		@outer('MySQL')
		def home():
		    print('from home')

		index()
		home()
		
		"""本质就是装饰器外加一个闭包函数，传入参数；函数名加括号优先级高于@语法糖执行顺序"""

```
### 三层语法糖
```PYTHON
# 判断七句print执行顺序
	def outter1(func1):
		print('加载了outter1')
		def wrapper1(*args, **kwargs):
			print('执行了wrapper1')
			res1 = func1(*args, **kwargs)
			return res1
		return wrapper1

	def outter2(func2):
		print('加载了outter2')
		def wrapper2(*args, **kwargs):
			print('执行了wrapper2')
			res2 = func2(*args, **kwargs)
			return res2
		return wrapper2

	def outter3(func3):
		print('加载了outter3')
		def wrapper3(*args, **kwargs):
			print('执行了wrapper3')
			res3 = func3(*args, **kwargs)
			return res3
		return wrapper3


	@outter1
	@outter2
	@outter3
	def index():
		print('from index')

	# 结果
	加载了outter3
	加载了outter2
	加载了outter1
	执行了wrapper1
	执行了wrapper2
	执行了wrapper3
	from index

```
## 函数补充
```python
# 递归函数
	官网、pycharm默认最大递归1000次  	# sys.getrecursionlimit()
			修改最大递归深度 	# sys.setrecursionlimit(2000)
	应用场景
		递推
			一层层往下推导答案(每次递归之后复杂度相较于之前一次有所下降)
		回溯
			依据最后的a1推导出最初需要的答案S(n=100有限值)
		
		"""一定要有结束条件"""

# 三元表达式
	定义格式：true_return if condition else false_return
	if 后条件成立返回，true_return，不成立返回false_return
	
	"当功能需求仅仅是二选一的情况下，推荐使用三元表达式，推荐不嵌套使用"

# 列表生成式
	"""给列表中的元素进行统一修改"""
		["%s_from_new" % name for name in name_list]
	进阶：列表生成式 + if
		["%s_from_new" % name for name in name_list if name != "alan"]

# enumerate枚举
	for i, j in enumerate(l1, start=1):
	    print(i, j)  # i为序号，y为l1列表中的元素，start控制起始的数字

# 其他生成式
	"""字典生成式"""
	{i: j for i, j in enumerate(name_list) if j != "alan"}  # 值得注意，此时alan对应的需要要是被删去，对应的数字不会往前进一位，仍保持去掉之前的状态
	"""集合生成式"""
	"""元组生成器，没有~~，为迭代器"""

# 匿名函数
	定义
		lambda 形参: 返回值
	使用
		(lambda x: x ** 2)(2)
		配合其他函数一起使用
			map()	映射
				l = [1, 2, 3]
				list(map(lambda x: x ** 2, l))  # 循环获取列表的值，并将其传入匿名函数处理
			zip()	拉链
				l1 = [11, 22, 33]
				l2 = ["alan", "tome", "jack"]
				zip(l1, l2)  # [(11, "alan"), (), ...]  # 以数据最短的为准！并且可以拉多个zip(l1, l2, l3)
			max()/min()	最大值/最小值
				本质是for循环取值，之后再比较大小
				在取字典中值最大值的时候 max(d, key=lambda x: l[x])
			filter()	过滤
				l1 = [11, 22, 33]
				filter(lambda x: x > 20, l).list  # [22, 33]
			reduce()	归总
				reduce(lambda x, y: x + y, l1)  # 第一次只拿2个数(11, 22), 然后求完和再拿(33， 33)

# 迭代器
	迭代
		迭代即更新换代，每次的更新都必须依赖于上一次的结果
	可迭代对象 → """迭代提供给我们不依赖于索引取值的方式，__next__()方法"""
		内置有__iter__方法的都称之为可迭代对象
	数据类型
		str、list、dict、tuple、set
		file<文件对象>
	迭代器对象  # 对标老母猪
		可迭代对象调用__iter__() 方法后
		d.__iter__ <=> iter(d)
		特点
			既含有__iter__方法 又含有__next__方法
			文件对象本身即是可迭代对象又是迭代器对象
			迭代器对象无论执行多少次__iter__之后，仍是迭代器对象
		__next__
			迭代器对象执行__next__方法其实就是迭代取值(类似于for)
	迭代取值与索引取值对比
		迭代取值
			优点：
				不依赖索引的一种通用取值方式
			缺点：
				取值顺序都是从左往右，不能回头
		索引取值
			缺点：
				需要提供有序容器类型的数据才能取值(不是一种通用的)
			优点：
				可以重复取值
	异常捕获
		异常捕获格式
			try:
			    被捕获的代码块
			except NameError:
			    异常nameerror类型发生后走的代码
			else:
			    当被检测的代码没有报错 正常运行结束后走这
			finally:
			    无论异常发不发生；都走这的代码
		断言assert
			name = "alan"
			assert isinstance(name, str)  # 断言后面为true，则不会报错；反之直接报错
		主动抛出异常  raise
			raise NameErrror
	for循环的本质(迭代器对象 + 异常捕获)
		def _my_for(data):
		while True:
	        res = data.__iter__()
		    try:
		        print(res.__next__())
		    except StopIteration:
		        # print('for循环结束')
		        break
# 生成器
	定义
		自定义迭代器
	格式
		def my_ge():
		    print("hellow")
		    yield 返回值
		res = my_ge()  # 第一次调用函数 并不会执行函数，而是将函数变成生成器
		ret = res.__next()  # 第二次执行调用__next__()函数函数执行到第一个yield停止，ret为yield后面的返回值
	yield传值
		res.send()
			干了两件事：一件事给yield传值，另一件是调用__next__()
	yield与return的对比
		yield
			可以返回值(支持多个并组织成元组)
			函数体代码遇到yield不会结束而是"停止"
			yield可以将函数变成生成器 并且支持外接传值
		return
			可以返回值(支持多个并组织成元组)
			函数体代码遇到return直接结束
	range本质
		def my_range(first_num, end_num=None, step=1):
		    if not end_num:
		        end_num = first_num
		        first_num = 0
		    while first_num < end_num:
		        yield first_num
		        first_num += step
		
		res = my_range(1, 10)  # 第一次并不会执行代码，转化为生成器
		for i in my_range(1, 10):
		    print(i)
	生成器表达式(母猪制造厂)
		形式上为"元组生成式"
		l = [11, 22, 33]
		res = (i + 1 for i in l if i != 11)  # res为产出的老母猪
		res.__next__()  # 12  下崽
		res.__next__()  # 23  下崽
```
## 常用内置函数
<div class="tablebox" style="overflow: auto;"><table border="1" style="display: table; width: 100% !important;"><thead valign="bottom">
<tr><th>&nbsp;</th><th>&nbsp;</th><th>Built-in Functions</th><th>&nbsp;</th><th>&nbsp;</th></tr>
</thead><colgroup> <col width="21%"> <col width="19%"> <col width="20%"> <col width="18%"> <col width="22%"> </colgroup>

<tbody valign="top">
<tr>
<td><a href="#abs" title="绝对值" rel="noopener"><span>abs()</span></a></td>
<td><a href="#func-dict" rel="noopener"><span>dict()</span></a></td>
<td><a href="#help" rel="noopener"><span>help()</span></a></td>
<td><a href="#min" rel="noopener"><span>min()</span></a></td>
<td><a href="#setattr" rel="noopener"><span>setattr()</span></a></td>
</tr>
<tr>
<td><a href="#all" rel="noopener" title="被判断的对象，里面只要有一个元素为False即为False，and"><span>all()</span></a></td>
<td><a href="#dir" rel="noopener" title="返回当前路径下名称空间内的名字"><span>dir()</span></a></td>
<td><a href="#hex" rel="noopener"><span title="十进制转为十六进制数">hex()</span></a></td>
<td><a href="#next" rel="noopener"><span>next()</span></a></td>
<td><a href="#slice" rel="noopener" title=""><span>slice()</span></a></td>
</tr>
<tr>
<td><a href="#any" rel="noopener" title="被判断的对象，里面只要有一个元素为True即为True，or"><span>any()</span></a></td>
<td><a href="#divmod" rel="noopener"  title="除法，结果为(整数部分, 余数部分)"><span>divmod()</span></a></td>
<td><a href="#id" rel="noopener"><span>id()</span></a></td>
<td><a href="#object" rel="noopener"><span>object()</span></a></td>
<td><a href="#sorted" rel="noopener"><span>sorted()</span></a></td>
</tr>
<tr>
<td><a href="#ascii" rel="noopener"><span>ascii()</span></a></td>
<td><a href="#enumerate" rel="noopener"><span>enumerate()</span></a></td>
<td><a href="#input" rel="noopener"><span>input()</span></a></td>
<td><a href="#oct" rel="noopener" title="十进制转为八进制数"><span>oct()</span></a></td>
<td><a href="#staticmethod" rel="noopener"><span>staticmethod()</span></a></td>
</tr>
<tr>
<td><a href="#bin" rel="noopener" title="十进制转为二进制数"><span>bin()</span></a></td>
<td><a href="#eval" rel="noopener" title="将字符串中的代码加载并执行，相较于exec，识别的较为简单"><span>eval()</span></a></td>
<td><a href="#int" rel="noopener"><span>int()</span></a></td>
<td><a href="#open" rel="noopener"><span>open()</span></a></td>
<td><a href="#func-str" rel="noopener"><span>str()</span></a></td>
</tr>
<tr>
<td><a href="#bool" rel="noopener"><span>bool()</span></a></td>
<td><a href="#exec" rel="noopener"  title="将字符串中的代码加载并执行"><span>exec()</span></a></td>
<td><a href="#isinstance" rel="noopener"  title="判断是否属于某个数据类型"><span>isinstance()</span></a></td>
<td><a href="#ord" rel="noopener" title="与chr功能相反，将字符转为ASCII码"><span>ord()</span></a></td>
<td><a href="#sum" rel="noopener" title="求和计数"><span>sum()</span></a></td>
</tr>
<tr>
<td><a href="#func-bytearray" rel="noopener"><span>bytearray()</span></a></td>
<td><a href="#filter" rel="noopener"><span>filter()</span></a></td>
<td><a href="#issubclass" rel="noopener"><span>issubclass()</span></a></td>
<td><a href="#pow" rel="noopener"  title="pow(4,3)  64"><span>pow()</span></a></td>
<td><a href="#super" rel="noopener"><span>super()</span></a></td>
</tr>
<tr>
<td><a href="#func-bytes" rel="noopener" title="字符类型转化为bytes类型数据"><span>bytes()</span></a></td>
<td><a href="#float" rel="noopener"><span>float()</span></a></td>
<td><a href="#iter" rel="noopener"><span>iter()</span></a></td>
<td><a href="#print" rel="noopener"><span>print()</span></a></td>
<td><a href="#func-tuple" rel="noopener"><span>tuple()</span></a></td>
</tr>
<tr>
<td><a href="#callable" rel="noopener" title="判断是否可调用，通俗点是否可加括号"><span>callable()</span></a></td>
<td><a href="#format" rel="noopener"><span>format()</span></a></td>
<td><a href="#len" rel="noopener"><span>len()</span></a></td>
<td><a href="#property" rel="noopener"><span>property()</span></a></td>
<td><a href="#type" rel="noopener"><span>type()</span></a></td>
</tr>
<tr>
<td><a href="#chr" rel="noopener" title="将ASCII码 传数字找字符"><span>chr()</span></a></td>
<td><a href="#func-frozenset" rel="noopener"><span>frozenset()</span></a></td>
<td><a href="#func-list" rel="noopener"><span>list()</span></a></td>
<td><a href="#func-range" rel="noopener"><span>range()</span></a></td>
<td><a href="#vars" rel="noopener"><span>vars()</span></a></td>
</tr>
<tr>
<td><a href="#classmethod" rel="noopener"><span>classmethod()</span></a></td>
<td><a href="#getattr" rel="noopener"><span>getattr()</span></a></td>
<td><a href="#locals" rel="noopener"><span>locals()</span></a></td>
<td><a href="#repr" rel="noopener"><span>repr()</span></a></td>
<td><a href="#zip" rel="noopener"><span>zip()</span></a></td>
</tr>
<tr>
<td><a href="#compile" rel="noopener"><span>compile()</span></a></td>
<td><a href="#globals" rel="noopener"><span>globals()</span></a></td>
<td><a href="#map" rel="noopener"><span>map()</span></a></td>
<td><a href="#reversed" rel="noopener"><span>reversed()</span></a></td>
<td><a href="#__import__" rel="noopener"><span>__import__()</span></a></td>
</tr>
<tr>
<td><a href="#complex" rel="noopener" title="复数调用"><span>complex()</span></a></td>
<td><a href="#hasattr" rel="noopener"><span>hasattr()</span></a></td>
<td><a href="#max" rel="noopener"><span>max()</span></a></td>
<td><a href="#round" rel="noopener"  title="四舍五入"><span>round()</span></a></td>
<td>&nbsp;</td>
</tr>
<tr>
<td><a href="#delattr" rel="noopener"><span>delattr()</span></a></td>
<td><a href="#hash" rel="noopener"><span>hash()</span></a></td>
<td><a href="#func-memoryview" rel="noopener"><span>memoryview()</span></a></td>
<td><a href="#func-set" rel="noopener"><span>set()</span></a></td>
<td>&nbsp;</td>
</tr>
</tbody>
</table></div>

## 模块

```python
# 什么是模块
	一系列功能的结合体

# 为什么要用模块
	提升开发效率

# 三种分类
	内置模块
		python解释器自带的
	第三方模块
		别人写好的 发布在网上的
	自定义模块
		自己写的

# 模块的四种表现形式
	使用python编写的代码(.py文件)
	已被编译为共享库或DLL的c或c++扩展
	包好一组模块的包(类似于文件夹，里面通常含有__init__.py文件)
	使用c编好并连接到python解释器的内置模块

# 两种调用方式
	import句式
		导入py文件模块，一定不能加后缀
		"""
		多次导入相同的模块 只会执行一次
		首次导入xxx模块发生的事
			1.运行导入文件(import句式.py)产生该文件的全局名称空间
			2.运行xxx.py文件
			3.产生xxx.py全局名称空间 运行xxx文件内代码 将产生的名字全部存档与xxx.py名称空间
			4.将导入文件名称空间产生一个xxx的名字指向xxx.py全局名称空间
		"""
		想要调xxx.py中的yyy方法，只需要xxx.yyy()即可运行
		知名道姓的调名称，不会产生名称冲突
		
		起别名
			import testtttttttttttttttttttttttt as t
	from xxx import yyy as <别名> 句式
		相较于import句式，这种句式指名道姓导名字，容易名称空间冲突
		通用导入
			from xxx import *
			__all__ = ['change_name', 'global_name']  # 在被导入的模块文件中可以使用__all__指定可以被导入的名字

# 判断py文件是作为模块文件还是执行文件
	__name__ = "__main__"  # 在执行文件中__name__的值是__main__；当文件为模块文件，则__name__为模块名
	"""避免循环导入问题"""

# 模块的导入顺序
	1.先从内存中找
	2.内置模块中查找
		在给py文件取名字的时候，避免与模块名一致
	3.sys.path系统路径中找
		结果中第一个元素为当前运行文件所在的文件路径
	
	当某个自定义模块查找不到时的解决方案
		1.自己手动将该模块所在的路径添加到sys.path中
		2.从执行文件开始，一级一级进行查找from...import...

# 绝对导入与相对导入
	# 获取项目顶级目录
		base_dir = os.path.dirname(os.path.dirname(__file__))  # 往上走一层的文件路径，找到顶级目录；防止除pycharm之外的程序启动
	"""在程序中涉及到多个文件之前导入模块的情况 一律按照执行文件所在的路径为准"""
	绝对导入
		始终按照执行文件所在的sys.path查找模块
	相对导入
		句点符，能够打破始终以执行文件为准的规则 只考虑两个文件之前的位置
		# 相对导入只能用在模块文件中 不能在执行文件中使用
```
## 正则模块re
```python
# 什么是正则表达式
	利用一些特殊符号的组合去字符串中筛选出符合条件的数据

# 字符组
	定义
		在同一个位置可能出现的各种符号组成的一个字符组，在正则中用[]表示
	特点
		使用中括号括起来  字符串默认只能单个字符匹配
	
	字符			描述			待匹配字符	匹配结果
	[0123456789]/[0-9]	表示0-9内的数字		2		True
	[a-z]			表示小写26字母		a		True
	[A-Z]			表示大写26字母		A		True
	[0-9a-zA-Z]		匹配所有的数字，小写大写字母	2eE		True

# 特殊字符
	特点
		默认也是单个字符匹配
		
	字符	描述
	.	匹配除换行符以外的任意字符
	\w	匹配字幕或数字、下划线
	\W	匹配非字母、非数字、非下划线
	\s	匹配空白符
	\S	匹配非空白符
	\d	匹配数字
	\D	匹配非数字
	\n	匹配一个换行符
	\t	匹配一个制表符
	\b	匹配一个单词的结尾
	^	匹配字符串的开始字符
	$	匹配字符串的结尾字符
		^$	组合使用精准匹配
	a|b	匹配字符a或字符b
	()	匹配括号内的表达式，也表示一个组
	[...]	匹配字符组中的字符
	[^...]	匹配除了字符组中字符的所有字符

# 量词
	特点
		表达式在没有量词修饰的情况下 都是单个单个匹配的
		量词必须结合(字符串、特殊符号等)一起使用 不能单独出现
		量词只能影响前面的一个表达式
		正则表达式中的量词默认都是"贪婪"匹配
	
	字符	描述
	*	重复零次或更多次
	+	重复一次或更多次
	？	重复零次或一次
	{n}	重复n次
	{n,}	重复n次或更多次
	{n,m}	重复n到m次
	
	"""贪婪匹配与非贪婪匹配"""
	.*  # 默认贪婪匹配 尽可能多的匹
	将贪婪匹配换为非贪婪匹配，只需在量词后面加?；非贪婪匹配并不是直接转换为0次了，而是由前后的限制决定
	正则表达式：<.*?>	数据：<div>asd</div>	==》	结果：<div>、</div>

# 取消转义符
	方式一：
		\\\\n  匹\\n
	方式二：
		在python中可以用r"\\n"

# ()分组相关
	res = re.search("^[1-9]\d{14}(\d{2}[0-9x])?$", '341111200001016611')
	print(res)  # 返回一个对象
	print(res.group())  # 341111200001016611
	print(res.group(1))  # 611  取超过范围的组数，会报错
	
	re.findall() 分组有限展示
		re.findall("^[1-9]\d{14}(\d{2}[0-9x])?$", '341111200001016611')
		print(res)  # ['611']
		re.findall("^[1-9]\d{14}(?:\d{2}[0-9x])?$", '341111200001016611')  # ?:取消分组优先展示

	# 有名分组
		?P<xxx>
		res = re.search("^[1-9]\d{14}(?P<xxx>\d{2}[0-9x])?$", '341111200001016611')
		print(res.group())  # 341111200001016611
		print(res.group(1))  # 611  取超过范围的组数，会报错  这种方法为索引取值
		print(res.group('xxx'))  # 通过名字取值

# re模块
	re.findall('正则表达式', '待匹配的文本')
		根据正则匹配出所有符合条件的数据
		res = re.findall('a', 'alan')
		print(res)  # ['a', 'a']  没查到返回空列表
	re.search('正则表达式', '待匹配的文本')
		根据正则匹配到一个符合条件的就结束
		res = re.search('a', 'alan')
		print(res)  # 产生一个结果对象，如果没有匹配到数据，返回None
		print(res.group())  # 真正的结果 ’a'
	re.match('正则表达式', '待匹配的文本')
		根据正则从头开始匹配(文本内容必须在开头匹配)
		res = re.match('a', 'alan')
		print(res)  # 产生一个结果对象，如果没有匹配到数据，返回None
		print(res.group())  # 真正的结果 ’a'
	re.split('正则表达式', '待匹配的文本')
		res = re.split('[ab]', 'abcd')
		print(res)  # ['', '', 'cd']  先按a分割，再按b分割
	re.sub('正则表达式', '字符', '待匹配的文本', 替换次数)
		res = re.sub('\d', 'L', 'alan6', 1)
		print(res)  # alanL  类似于字符串内置方法replace，替换次数默认不写替换全部
	re.subn('正则表达式', '字符', '待匹配的文本', 替换次数)
		res = re.sub('\d', 'L', 'alan6', 1)
		print(res)  # ('alanL', 1)  返回一个元组，告诉替换几个
	obj = re.compile('正则表达式')
		res = obj.search('待匹配的文本')
	re.finditer('正则表达式', '待匹配文本')
		res = re.finditer('\d+', 'alan123alan12')
		print(res)  # 返回一个可迭代对象
		print([i.group() for i in res])  # 找不到也不报错[]
	
```
## collections模块
```python
from collections import namedtuple
# 具名元组namedtuple
	生成可以使用名字来访问元素内容的tuple
	eg:
		point = namedtuple('坐标', ["x", "y"])  # ["x", "y"] <=> 'x y'
		res = point(11, 22)
		print(res)	坐标(x=11, y=22)
		print(res.x)	11
		print(res.y)	22

# 队列模块
	import queue  # 内置队列模块:FIFO
	# 初始化队列
	q = queue.Queue()
	# 往队列添加元素
	q.put('first')
	q.put('second')
	# 从队列中获取元素
	print(q.get())  "first"
	print(q.get())  "second"
	print(q.get())  值取没了  原地等待
	
# 双端队列deque
	q = deque([11, 22, 33])
	q.append(44)  # deque([11, 22, 33, 44])
	q.appendleft(55)  # deque([55, 11, 22, 33, 44])  从左侧添加
	print(q.pop())  # 从右侧取值
	print(q.popleft())  # 从左侧取值

# 有序字典OrderedDict
	排序规则
		字典的key会按照插入的顺序排列，不是key本身排序
	info = {"name": "alan", "age": 18}
		定义的字典是无序的
	order_dict = OrderedDict([('name': 'alan'), ('age', 18)])
	
# 默认值字典defaultdict
	ll = [11, 22, 33, 44]
	{"k1": [], "k2": []}  # 将ll中大于22的元素放在k2中
	 my_dict = defaultdict(list)

# 计数器
	res = 'asdasdasdaasd'
	ret = Counter(res)  # Counter({'a': 5, 'b': .....})
```
## time模块
```python
# 时间的三种表现形式
	1.时间戳timestamp
	2.结构化时间strut_time
		一般给机器看的
	3.格式化时间format time
		2022-01-01 00:00:00

# struct_time元组元素结构
	属性                            值
	tm_year（年）                  比如2011 
	tm_mon（月）                   1 - 12
	tm_mday（日）                  1 - 31
	tm_hour（时）                  0 - 23
	tm_min（分）                   0 - 59
	tm_sec（秒）                   0 - 61
	tm_wday（weekday）             0 - 6（0表示周日）
	tm_yday（一年中的第几天）        1 - 366
	tm_isdst（是否是夏令时）        默认为-1

# time模块方法
	time.sleep(secs)
	time.time()  # 时间戳
	time.gmtime()  # 结构化时间，本初子午线时间
	time.localtime()  # 结构化时间，本地时间-东八区
	time.strftime('%Y-%m-%d %H:%M:%S')  # 获取本地格式化时间

# 时间类型之前相互转换
```
![image](https://img2022.cnblogs.com/blog/2358523/202207/2358523-20220731011523751-412930294.png)
## datetime模块
```python
# 内置方法
	datetime.date.today()		# 2022-01-01
	datetime.datetime.today()	# 2022-01-01 00:00:00.000000
	datetime.datetime.now()  # 同上一个方法，当前时间
	datetime.datetime.utcnow()  # 国际时间

	res = datetime.datetime.today()
	year = res.year
	month = res.month
	day = res.day

# 时间差(timedelta)
	ctime = datetime.datetime.today()  # 获取当前时间
	time_tel = datetime.timedelta(days=3)  # 相差三天
	print(ctime - time_tel)  # 打印三天前的这个时间点
```
## random模块(随机数模块)
```python
import random
	random.random()
		随机产生一个0-1之间的小数
	random.randint(1, 6)  # 包括前后边界
		随机产生1-6之间的整数
	random.uniform(1, 6)
		随机产生一个1-6之间的小数
	random.choice(["特等奖", "一等奖", "二等奖"])
		随机抽取一个
	random.sample(["安徽省", "江苏省", "浙江省", "上海市"], 2)
		随机在样本中抽取两个样本，返回列表
	random.shuffle(l)
		随机打乱容器类型中的诸多元素

# 练习题---随机五位验证码
	code = ''
	for i range(5):
	    random_int = str(random.randint(0, 9))
	    random_upper = chr(random.random(65, 90))
	    random_lower = chr(random.random(97, 122))
	    temp = random.choice([random_int, random_upper, random_lower])
	    code += temp
```
## os模块
```python
"""与操作系统打交道"""
import os
	os.mkdir("单级目录")
		创建单层目录，创建多级目录时会报错
	os.makedirs(r"一级目录\二级目录\...")
		创建多级目录
	os.rmdir("空目录")
		删除空目录
	os.removedirs("多级空目录")
		删除多级空目录
	os.remove("a.txt")
		删除a文件
	os.rename("老文件名", "新文件名")
		修改文件名称
	os.listdir("路径")
		列举当前路径所在目录下所有的文件名，空默认为当前路径
	os.path.dirname(__file__)
		当前文件路径，嵌套使用作为上一层的路径
	os.path.join()
		专门用于路径拼接，自动识别当前操作系统的路径分隔符
	os.getcwd()
		获取当前工作路径
	os.chdir()
		切换路径
	os.path.exists()
		判断当前目录、文件是否存在
	os.path.isfile()
		判断当前路径是否是一个文件
	os.path.isfir()
		判断当前路径下是否是目录
	os.getsize(path)
		获取文件字节数
```
## sys模块
```python
"""跟python解释器打交道"""
import sys
	sys.path
		列表，环境变量有关
	sys.version
		当前解释器版本
	sys.platform
		WIN32
	sys.argv
		获取当前执行文件的绝对路径
		
		python "D:\python\test test.py" 111 222
		>>> [D:\python\test test.py", "111", "222"]
		sys.argv[1], sys.args[2]  # 用于接受账号密码
```
## json序列化模块
```python
# 原理
	将其他数据转化为字符串 >>> 将字符串转化成json格式 >>> 转换为二进制基于网络传输
	将基于网络传输来的二进制转化为中json格式 >>> 将json格式转化为个钟类型数据

# python其他类型数据转化为json格式字符串(序列化)
	res = json.dumps(data)  # {"name": "alan"}  双引号为json类型表示
	数据内容中出现中文，可以用ensure_ascii=False规避掉
# 将json格式化字符串转化为某种数据类型(反序列化)
	json.loads(res)

# Supports the following objects and types by default:
	# 集合不能呦！！！
	+-------------------+---------------+
	| Python            | JSON          |
	+===================+===============+
	| dict              | object        |
	+-------------------+---------------+
	| list, tuple       | array         |
	+-------------------+---------------+
	| str               | string        |
	+-------------------+---------------+
	| int, float        | number        |
	+-------------------+---------------+
	| True              | true          |
	+-------------------+---------------+
	| False             | false         |
	+-------------------+---------------+
	| None              | null          |
	+-------------------+---------------+

# 文件操作的两种方法补充
	dump(序列化对象，文件)
	load(序列化对象，文件)
	这两个方法是对dumps和loads的简写，实现将字典序列化写入文件和反序列化取出
```
## hashlib模块
```python
# 加密
	将明文数据通过一系列算法变成密文数据，目的是为了数据的安全；密文数据越长表示内部算法越复杂，对应破解算法的难度也就越多

# 算法
	md系列、sha系列、base系列

# 基本使用
	1.先确定算法类型(md5普遍使用)
		md5 = hashlib.md5()
	2.将明文数据传输给md5算法(update只能接受bytes类型数据)
		md5.update("123".encode('utf8'))
	3.获取加密之后的密文数据(没有规则的一串随机字符串)
		res = md5.hexdigest()
		print(res)

"""加密之后的密文数据是没有办法反解密成明文数据的"""

# 文件效验
	"""明文数据可以分开传，只要数据一致，最后的密文也是一致"""
	md5.update("1".encode('utf8'))
	md5.update("2".encode('utf8'))
	md5.update("3".encode('utf8'))  <=>  md5.update("123".encode('utf8'))
	如果一个文件特别大
		随机抽取文件的几个数据片段进行加密
		res = os.path.getsize("路径")
		read_method = [0, res // 4, res // 2, res]  # 介个seek移动光标

# 加盐处理
	在对明文数据中做一些干扰项，在对其进行加密
	动态加盐
		当前时间 用户名的部分  uuid(随机字符串(永远不会重复))
```
## subprocess模块(子进程模块)
```python
"""类似于远程操作工具，xshell写好了"""
	import subprocess
	# 当前系统中正在运行的进程
	res = subprocess.Popen('tasklist',  # 执行命名
	                       shell=True,
	                       stdout=subprocess.PIPE,  # 基于管道传输
	                       stderr=subprocess.PIPE
	                       )
	print('stdout',res.stdout.read().decode('gbk'))  # 获取正确命令执行之后的结果
	print('stderr',res.stderr.read().decode('gbk'))
	'''windows电脑内部编码默认为GBK'''

```
## logging日志模块
```python
import logging

# 日志的五个等级
	logging.debug()		10
	logging.info()		20
	logging.warning()	30
	logging.error()		40
	logging.critical()	50
	"""默认记录的级别在30及以上"""
	
# 简单实用
	import logging
	
	file_handler = logging.FileHandler(filename='x1.log', mode='a', encoding='utf-8')
	logging.basicConfig(
	    format = '%(asctime)s - %(name)s - %(levelname)s - %(module)s: %(message)s',
	    datefmt = '%Y-%m-%d %H:%M:%S %p',
	    handlers = [file_handler,],
	    level = logging.ERROR
	)
	
	logging.error("TEST ERROR")
	
# 详细使用
	import logging
	# 1.logger对象:负责产生日志
	logger = logging.getLogger('转账记录')
	# 2.filter对象:负责过滤日志(直接忽略)
	# 3.handler对象:负责日志产生的位置
	hd1 = logging.FileHandler('a1.log',encoding='utf8')  # 产生到文件的
	hd2 = logging.FileHandler('a2.log',encoding='utf8')  # 产生到文件的
	hd3 = logging.StreamHandler()  # 产生在终端的
	# 4.formatter对象:负责日志的格式
	fm1 = logging.Formatter(
		fmt='%(asctime)s - %(name)s - %(levelname)s -%(module)s:  %(message)s',
		datefmt='%Y-%m-%d %H:%M:%S %p',
	)
	fm2 = logging.Formatter(
		fmt='%(asctime)s - %(name)s %(message)s',
		datefmt='%Y-%m-%d',
	)
	# 5.绑定handler对象
	logger.addHandler(hd1)
	logger.addHandler(hd2)
	logger.addHandler(hd3)
	# 6.绑定formatter对象
	hd1.setFormatter(fm1)
	hd2.setFormatter(fm2)
	hd3.setFormatter(fm1)
	# 7.设置日志等级
	logger.setLevel(30)
	# 8.记录日志
	logger.debug('写了半天 好累啊 好热啊')

# 日志配置
	# 核心就在于CV
	import logging
	import logging.config

	standard_format = '[%(asctime)s][%(threadName)s:%(thread)d][task_id:%(name)s][%(filename)s:%(lineno)d]' \
					  '[%(levelname)s][%(message)s]' #其中name为getlogger指定的名字

	simple_format = '[%(levelname)s][%(asctime)s][%(filename)s:%(lineno)d]%(message)s'

	logfile_path = 'a3.log'
	# log配置字典
	LOGGING_DIC = {
		'version': 1,
		'disable_existing_loggers': False,
		'formatters': {
			'standard': {
				'format': standard_format
			},
			'simple': {
				'format': simple_format
			},
		},
		'filters': {},  # 过滤日志
		'handlers': {
			#打印到终端的日志
			'console': {
				'level': 'DEBUG',
				'class': 'logging.StreamHandler',  # 打印到屏幕
				'formatter': 'simple'
			},
			#打印到文件的日志,收集info及以上的日志
			'default': {
				'level': 'DEBUG',
				'class': 'logging.handlers.RotatingFileHandler',  # 保存到文件
				'formatter': 'standard',
				'filename': logfile_path,  # 日志文件
				'maxBytes': 1024*1024*5,  # 日志大小 5M
				'backupCount': 5,
				'encoding': 'utf-8',  # 日志文件的编码，再也不用担心中文log乱码了
			},
		},
		'loggers': {
			#logging.getLogger(__name__)拿到的logger配置  空字符串作为键 能够兼容所有的日志
			'': {
				'handlers': ['default', 'console'],  # 这里把上面定义的两个handler都加上，即log数据既写入文件又打印到屏幕
				'level': 'DEBUG',
				'propagate': True,  # 向上（更高level的logger）传递
			},  # 当键不存在的情况下 (key设为空字符串)默认都会使用该k:v配置
		},
	}
	# 使用配置字典
	logging.config.dictConfig(LOGGING_DIC)  # 自动加载字典中的配置
	logger1 = logging.getLogger('xxx')
	logger1.debug('好好的 不要浮躁 努力就有收获')

# log文件和终端同时打印
	
# log文件详细、终端简单
```
## 第三方模块
```python
# 并不是python自带的 需要基于网络下载!!!

'''pip所在的路径添加环境变量'''
下载第三方模块的方式
    方式1:命令行借助于pip工具
        pip3 install 模块名  # 不知道版本默认是最新版
        pip3 install 模块名==版本号  # 指定版本下载
        pip3 install 模块名 -i 仓库地址  # 临时切换
        '''命令行形式永久修改需要修改python解释器源文件'''
    方式2:pycharm快捷方式
        settings
        	project
            	project interprter
                	双击或者加号
        点击右下方manage管理添加源地址即可
# 下载完第三方模块之后 还是使用import或from import句式导入使用
"""
pip命令默认下载的渠道是国外的python官网(有时候会非常的慢)
我们可以切换下载的源(仓库)
    （1）阿里云 http://mirrors.aliyun.com/pypi/simple/
    （2）豆瓣 http://pypi.douban.com/simple/
    （3）清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/
    （4）中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/
    （5）华中科技大学http://pypi.hustunique.com/

pip3 install openpyxl -i http://mirrors.aliyun.com/pypi/simple/
"""


"""
下载第三方模块可能报错的情况及解决措施
	1.报错的提示信息中含有关键字timeout
		原因:网络不稳定
		措施:再次尝试 或者切换更加稳定的网络
	2.找不到pip命令
		环境变量问题
	3.没有任何的关键字 不同的模块报不同的错
		原因:模块需要特定的计算机环境
		措施:拷贝报错信息 打开浏览器 百度搜索即可
			pip下载某个模块报错错误信息
"""
```
## 包
```python
# 包的定义
	包就是一个包含__init__.py文件的文件夹
	
# 包的本质
	本质就是模块的一种形式，包是用来被当成模块来导入的

# 包的结构
	sound/                          Top-level package
	      __init__.py               Initialize the sound package
	      formats/                  Subpackage for file format conversions
	              __init__.py
	              wavread.py
	              wavwrite.py
	              aiffread.py
	              aiffwrite.py
	              auread.py
	              auwrite.py
	              ...
	      effects/                  Subpackage for sound effects
	              __init__.py
	              echo.py
	              surround.py
	              reverse.py
	              ...
	      filters/                  Subpackage for filters
	              __init__.py
	              equalizer.py
	              vocoder.py
	              karaoke.py
	              ...

# 导入包
	导入包还是使用import、from/import句式

	1.首次导入模块会发生3件事：

		被导入模块产生一个名称空间
		执行被导入的py文件，然后把执行的数据都丢到名称空间中
		执行文件中产生一个变量指向这个名称空间

	2.首次导入包会发生3件事：

		产生一个包的名称空间
		执行被导入包下的 __ init __.py文件，然后把执行的数据都丢到包的名称空间中
		执行文件中产生一个变量指向这个包的名称空间

	3.包也可以被认为是“模块”，可直接导入
```
## 软件开发规范
```python
'''目录规范并无固定的要求 只需清晰可读即可'''

# 文件分类详细
	bin文件夹：
		存放一系列启动文件，当启动文件很少或者只有一个的时候可以写在外边>>>start.py
	conf文件夹：
		存放一系列的配置文件，一般情况该文件内的变量名都是大写>>>settings.py
	lib文件夹：
		存放公共的功能(第三方)>>>common.py
	db文件夹：
		存放数据相关文件>>>userinfo.txt
	log文件夹：
		存放日志记录文件>>>log.txt
	core文件夹(src文件夹)：
		存放项目核心代码文件>>>src.py
	README.md:
		存放说明相关信息（类似于说明书，广告，章程···）
	requirements.txt文件：
		存放项目所需的第三方模块及版本号
```
