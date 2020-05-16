# Spark Streaming

This Tutorial is based on https://www.dezyre.com/apache-spark-tutorial/spark-tutorial; 

1) Prerequisites
- CentOS 7 or Ubuntu
- Java Developer Kit JDK 8 
- Scala

2) Spark 
- Download Apache Spark Hadoop 2.7 (wget https://downloads.apache.org/spark/spark-2.4.5/spark-2.4.5-bin-hadoop2.7.tgz)
- Create textfile based on input.txt

3) Work with Spark (Line Count)
- Start Spark-Shell
$ ./bin/spark-shell

- Insert textfile into Scala
$ scala> val input = sc.textFile("input.txt")

3.1) Count Lines: scala>input.count()

- Word Count (https://dzone.com/articles/wordcount-with-spark-and-scala)
- Create a scala function 
$ nano WordCountScala.scala

- Type function code
$ val input = sc.textFile("input.txt")
$ val count = input.flatMap(line => line.split (" "))
$ .map(word => (word,1))
$ .reduceByKey(_+_)

- Run wordcountscala.scala in spark-shell
$ ./bin/spark-shell -i WordCountScala.scala

- Show function output)
$ scala> count.collect

3.2) Show total number of words (exclude doubles)
$ scala> count.count()

3.3) Count words in total
- Open your scala function
$ nano WordCountScala.scala

- Add the following function code
$ val words = input.flatMap(line => line.split(" ")
$ .map(word => (word))

- Run WordCountScala.scala in Spark-Shell
$ ./bin/spark-shell -i WordCountScala.scala

3.4) Show total no of words of a document
$ scala> words.collect

3.5) Show total no of words incl multiples
$ scala> words.count()



