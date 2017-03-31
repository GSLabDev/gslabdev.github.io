---
layout: post
title: "Pepper-Box Load Generator"
date: 2017-03-31 16:54:46
author: Satish Bhor
categories:
- blog
- Kafka
- Development
img:
thumb: thumb02.jpg
---

<b>Pepper-Box</b> is a Kafka load generator application which can be used as plugin for JMeter or standalone utility. 

It allows to send kafka messages of type plain text(JSON, XML, CSV or any other custom format) as well as java serialized objects. 
Pepper-Box includes template engine and random data generation function which helps to design message in any format. 

If we use it with JMeter then we can use all JMeter features. Pepper-Box is very useful in streaming analytics and data pipelines 
implementation, where input data format is tightly coupled with business problems. <!--more-->

**Pepper-Box include four main components:**

**Pepper-Box Kafka Sampler :**


This is JMeter java sampler and acts as kafka producer.This sampler gets messages from backend data generator and sends messages to 
kafka broker at given throttled rate.If Kafka broker is designed with data encryption using SSL/TLS and authentication using Kerberos 
then these securities can be easily configured in this sampler. By default we included required and tuning related parameters but 	
It provides user interface to configure other kafka producer parameters as well.


**Pepper-Box PlainText Config Element :** 	


This JMeter config element generates plaintext messages for Kafka sampler based on input message schema designed using template engine. 
This config element provides user interface to enter message schema template. Before test starts this config elements takes schema,
processes it and creates plain text message iterator which generates a millions of plain text messages per second.


**Pepper-Box Serialized Config Element :** 


This JMeter config element generates serialized object messages for kafka sampler based on input class and its field mappings with template
functions.This config element element takes class name and its field mappings with random data generation functions, process it and creates 
Java object iterator which generates a millions of serialized object messages per second.


**Pepper-Box Console Load Generator :**


This is standalone kafka load generator and does not require Jmeter. This feature currently only supports plain text message generation 
and java serialized message generation is in feature scope. This console based load generator takes required details message schema file,
producer property file, throttle rate, duration, number of producer threads etc. and starts generating load at given throttled rate.


You can see below sample JSON message schema with five fields and values are template functions which will be replaced with generates 
random values dynamically for every iteration,

```
{
"messageId":{{SEQUENCE("messageId", 1, 1)}},
"messageBody":"{{RANDOM_ALPHA_NUMERIC("abcdefg", 2)}}",
"messageCategory":"{{RANDOM_STRING("Finance","Shares","Healthcare")}}", "messageStatus":"{{RANDOM_STRING("Accepted","Pending","Processing")}}",
"messageTime":{{TIMESTAMP()}}
}
```

**Pepper-Box workflow**


When we enter input schema(sample schema shown above) and start test, then Pepper-Box follows series of steps before producing actual load 
on kafka.

1. Schema is given as input to schema parser which parses schema and prepares series of expressions
2. Schema translator then converts those series of expressions into a class.
3. Then translated java class compiled and intentioned as message iterator.
4. To produce messages on kafka this message iterator is iterated for specified test duration.


