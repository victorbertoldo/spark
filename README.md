# Spark

## SparkSession
O primeiro componente de uma aplicação Spark é o `SparkContext`, pois ele é principal ligação entre qlqr funcionalidade aplicação Spark ao cluster Spark, ou seja ele é o que conecta o cluster à aplicação.

Para utilizar o `SparkContext`, é necessário utilizar um objeto de configuração, este objeto é o `SparkConf`, nele nós definimos o nome da aplicação, o master node do Spark, bem como outras configurações existentes na documentação.

_Exemplo de uso_:
``` python
from pyspark import SparkContext, SparkConf

configure = SparkConf().setAppName("Teste02").setMaster("spark://<nomedamaquina>:7077")

sc = SparkContext(conf = configure)
```
> Note que é necessário adicionar o master utilizando a porta de comunicação interna do Spark (7077)

Mas se vamos usar somente o Spark SQL (DataFrames), nós importamos apenas a sessão do Spark, e utilizamos o `builder` para setar as configurações:

_Exemplo de uso_:
``` python
from pyspark.sql import SparkSession

spark = SparkSession \
    .builder \
    .master("spark://<nomedamaquina>:7077") \
    .appName("First Spark SQL code") \
    .enableHiveSupport() \
    .getOrCreate()
```
> GetOrCreate significa q se já houver uma sessão spark ativa, os parametros dela serão sobrescritos para as novas configurações, inves de iniciar um novo cluster job.


https://zacks.one/aws-emr-lab/

