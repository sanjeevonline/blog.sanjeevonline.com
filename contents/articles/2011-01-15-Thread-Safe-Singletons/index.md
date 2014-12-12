---
template: article.jade
title: Best practices for threadsafe Singletons
date: 2011-01-15 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices, technology]
excerpt: A singleton class should be designed to ensures that there exists only one instance per application. Special care must be taken if your application is deployed on a clustered environment as in this case it is possible that multiple instance of your singleton class are available in your application.
---
A singleton class should be designed to ensures that there exists only one instance per application. Special care must be taken if your application is deployed on a clustered environment as in this case it is possible that multiple instance of your singleton class are available in your application.   

Here are a few ways to create a thread safe singleton classes in your application. 

<span class="more"></span>

<h3>1. Lazy loading Singleton instance - Using Synchronized method or block</h3>

	public class SingletonClass{
    	private SingletonClass sc;
    	private SingletonClass(){}

   	 	public static SingletonClass getInstance(){
        	synchronized(SingletonClass.class) {
              if (sc == null) {
                  sc = new SingletonClass();
              } else {
                 return sc;
              }
        	}
    	}
	}

<b>Issues</b>:	The use of synchronized keyword in a singleton class means that only one thread will be executing the synchronized block at a time and all other threads would be waiting.
		
<h3>2. Early initialization Singleton - Using Static Member Variable</h3>

	public class SingletonClass{
    	private static sc = new SingletonClass();
    	private SingletonClass(){}

	    public static SingletonClass getInstance(){
    	    return sc;
    	}
	}
	
This approach is also known as early initialization because we are creating the singleton instance at an early stage and not when the instance is actually needed by another class.

<b>Issues</b>: The use of static member variable means that this singleton instance will be created as soon as the class is loaded by any Classloader in JVM. 
	 
<h3>3. Singleton using Inner Classes</h3>
	
	public class SingletonClass{
    	private SingletonClass(){}
    	private static class InstanceHolder{
        	private static final SingletonClass INSTANCE = new SingletonClass(); 
    	}
    	public static SingletonClass getInstance(){
        	return InstanceHolder.INSTANCE; //line1
    	}
	}
	
Here the instance is being created on demand and is also thread safe. The use of inner classes helps in the sense that the very first time singleton object is requested, the inner class is loaded by line1 and this loading of inner class causes the static member variable to be created and returned. Next time, the singleton member variable is requested causes the same static reference variable to be returned.

<h3>4. Singleton using enums</h3>

	public enum Singleton{
    	INSTANCE;
    	private int a;
    	public int getA() {
        	return a;
    	}
	}
	
To get a single instance of this enum one should use:

	Singleton.INSTANCE
	
To get the value of member variable a, one should use:
	
	Singleton.INSTANCE.getA();
	
<b>In my experience using enums is the best way to implement Singleton design pattern in any Java application. It is thread safe and also provides lazy initialization.</b>
