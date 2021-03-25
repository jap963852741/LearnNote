# java中实现多线程有两种方式

## 继承Thread类
* 重写其run方法。
* ![image](https://user-images.githubusercontent.com/32256068/112435044-31c09600-8d7f-11eb-9b83-b55895e0adf5.png)
* ```
	public static void main(String[] args) {
		A a = new A();
		a.start();
	}


## 实现Runnable接口
* 重写run方法
* 然后和一个线程绑定
* ![image](https://user-images.githubusercontent.com/32256068/112435848-3b96c900-8d80-11eb-8376-ab55daf5e39f.png)
* ```
	public static void main(String[] args) {
		B b = new B();
		Thread threadForB = new Thread(b);
		threadForB.run();
  }
