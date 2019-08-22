- Qual o objetivo do comando cache em Spark?

O objetivo do comando cache é melhorar a eficiência do código permitindo que resultados intermediários de operações lazy possam ser armazenados e reutilizados repetidamente.

- O mesmo código implementado em Spark é normalmente mais rápido que a implementação equivalente em MapReduce. Por quê?

Sim, pois o Spark permite que resultados intermediários sejam passados diretamente entre as operações a serem executadas através do caching de dados em memória e também porque várias operações podem ser executadas sobre um mesmo conjunto de dados em cache

- Qual é a função do SparkContext?

Armazenamento de configurações que vão ser utilizadas na alocação de recursos, como memória e processadores, criação de RDDs, iniciar a execução de jobs, criação de variáveis

- Explique com suas palavras o que é Resilient Distributed Datasets (RDD).

Ele é o objeto principal do modelo de programação do Spark, pois são nesses objetos que serão executados os processamentos dos dados com a função principal de captar os dados do Spark

- GroupByKey é menos eficiente que reduceByKey em grandes dataset. Por quê?

Pois com o groupByKey os cálculos de resultados parciais não é realizado, trazendo um volume de dados maior desnecessariamente podendo atingir a quantidade de memória disponível e ser necessário a escrita dos dados em disco impactanto negativamente a performance.

- Explique o que o código Scala abaixo faz.
      val textFile = sc.textFile("hdfs://...")
      val counts = textFile.flatMap(line => line.split(" "))
      .map(word => (word, 1))
      .reduceByKey(_ + _)
      counts.saveAsTextFile("hdfs://...")

É lido um arquivo de texto quebrando cada linha e gerando um grupo de palavras, após isso as palavras são transformadas em chaves e inicia-se a contagem de cada palavra gerando um arquivo de texto no final com o resultado.
