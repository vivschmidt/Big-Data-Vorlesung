## Spark Streaming

# This Tutorial is based on https://www.dezyre.com/apache-spark-tutorial/spark-tutorial
# Download Apache Spark Hadoop 2.7
wget https://downloads.apache.org/spark/spark-2.4.5/spark-2.4.5-bin-hadoop2.7.tgz 
# Create a TextFile: input.txt  (see: https://www.dezyre.com/apache-spark-tutorial/spark-tutorial)
# Insert text
nano input.txt
# text example "In as name to here them deny wise this. As rapid woody my he me which. Men but they fail shew just wish next put. Led all visitor musical calling nor her. Within coming figure sex things are. Pretended concluded did repulsive education smallness yet yet described. Had countryman his pressed shewing. No gate dare rose he. Eyes year if miss he as upon."

I. Line Count

#Start Spark-Shell
./bin/spark-shell
#Insert TestFile into Scala
scala> val input = sc.textFile("input.txt")
#Count Lines
scala>input.count()

II. Word Count
#Counts how often words are used in a document
#Create a scala function https://dzone.com/articles/wordcount-with-spark-and-scala
nano WordCountScala.scala
#type function code
val input = sc.textFile("input.txt")
val count = input.flatMap(line => line.split (" "))
.map(word => (word,1))
.reduceByKey(_+_)
#run wordcountscala.scala in spark-shell
./bin/spark-shell -i WordCountScala.scala
#run commmand count.collect (to show the functions output)
scala> count.collect

#run command count.count() - to see the toatl number of words (without double)
scala> count.count()

#total word count
#open your scala function
nano WordCountScala.scala

#add the following function code
val words = input.flatMap(line => line.split(" ")
.map(word => (word))

#run WordCountScala.scala in Spark-Shell
./bin/spark-shell -i WordCountScala.scala

#Rund command words.collect (shows you the total words of the document)
scala> words.collect

#rund command words.count() - see the total number of words (incl multiples)
scala> words.count()



