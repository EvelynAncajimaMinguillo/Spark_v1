## Spark_v1
Contador de palabras en Scala utilizando Spark

### Comandos Spark con Scala
val textFile = sc.textFile("file:///spark/spark-2.2.1-bin-hadoop2.7/README.md")

val tokenizedFileData = textFile.flatMap(line=>line.split(" "))

var countPrep = tokenizedFileData.map(word=>(word,1))

val counts = countPrep.reduceByKey((accumValue, newValue) => accumValue + newValue)

val sortedCounts = counts.sortBy(KvPair => KvPair._2, true)

sortedCounts.saveAsTextFile("file:///D:/APRENDER/Spark")
