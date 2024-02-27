---
title: firstCommit
comments: false
type: tags
tags:
  - 2022
categories: 生活
keywords: '生活,入门'
description: 我的第一篇博客，我会变得更好。
cover: 'https://momentum.photos/img/a786c1bc-03c4-4f4b-93ca-5b3649146ed0.jpg'
abbrlink: 28741
date: 2022-01-12 14:46:14
---

spring加载过程

```java
//测试spring的bean定义和加载  testBeanInit("spring say hello!");
    public static void testBeanInit(String str){
        DefaultListableBeanFactory defaultListableBeanFactory = new DefaultListableBeanFactory();
        BeanDefinition beanDefinition = new GenericBeanDefinition();
        //注册beandefinition
        beanDefinition.setBeanClassName("com.dn.bean.Account");
        defaultListableBeanFactory.registerBeanDefinition(account,beanDefinition);
        //通过反射获取bean
        Account account = ((Account) defaultListableBeanFactory.getBean(FileStream.account));
        account.setRealname("大黄鸭");
        System.out.println(JSONObject.toJSONString(account));
        account.test(str);

    }
```



