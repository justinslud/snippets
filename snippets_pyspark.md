# session
from pyspark.sql import SparkSession
spark = SparkSession.builder.getOrCreate()

# start
from pyspark import SparkContext
sc =SparkContext()
x = sc.parallelize(stuff) # breaks into partitions

# map


# sort
df.sort(F.desc('avg(column)'')

# dataframe (from text, json, csv, rdd)
from pyspark.sql import Row

df = spark.read.csv(fp, headers=True, schema=schema)

# io
words = sc.textFile("/usr/share/dict/words")

df.write.csv('name.csv')

# schema
from pyspark.sql import StructType, StringType, StructField, BoolType, DoubleType
schema = StructType([StructField("firstname",StringType(),canbenull=True), ...])

# filter
df.filter((df.age < 50) | ((df.age > 90) & (df.alive == True)))
df.filter(col('age') < 50)

df.where()

# data manipulation
df.select('salary').show() # like pandas df[[cols]]

df.corr('salary', 'id')	

# showing
df.describe().show(n=)

df.columns
df.printSchema()

# columns
df.withColumn(name, data) # makes new column

df.withColumnRenamed(old, new) # renames column

# query
df.createOrReplaceTempView("PERSON_DATA")
df2 = spark.sql("SELECT * from PERSON_DATA where salary > 3000")

# pandas
df.toPandas()

# join
df.join(df2, df1.thing == df2.otherthing, 'left_outer') # and other types

# grouping
df.groupBy('thing').agg({'colname', 'mean'})

# machine learning

from pyspark.ml.regression import LinearRegression
from pyspark.ml.feature import VectorAssembler
from pyspark.ml.linalg import Vectors
from pyspark.ml.clustering import KMeans

va = VectorAssembler(inputCols=['var1', 'var2'], outputCol=['y'])
vcluster_df = va.transform(df)

km = KMeans()
km.setK(3).setSeed(seed)
kmodel = km.fit(vcluster_df)

