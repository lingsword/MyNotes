## 测试


```java
class Person{
	//属性，或者变量
	String name;
	boolean isMarried;
	//构造器
	public Person(){};
	public Person(String n,boolean im){
		name = n; isMarried = im;
	}
	//方法，或者函数
	public void walk(){
		System.out.println("人走路...");
	}
	public String display(){
		return "名字是："+name+",Married:"+isMarried;
	}
	//代码块
	{
		name = "Hanguo";
		age = 19;
		isMarried = true;
	}
	//内部类
	class pet(){
		String name;
		float weight;
	}
}
```
