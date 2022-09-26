# Treinando_Spark_com_Pyspark
-------------------------------------------------------------------------------
## Configuração de Ambiente: 
-------------------------------------------------------------------------------
 Instalar uma JDK que vai permitir rodar código na linguagem Scala nas JVM (que é como o Spark foi construído):<br>
 !apt-get install openjdk-8-jdk-headless -qq > /dev/null
 
 Baixar os arquivos do Spark na máquina virtual do Google. versão 3.1.2 do Spark e a versão 2.7 do Hadoop:<br>
 !wget -q https://archive.apache.org/dist/spark/spark-3.1.2/spark-3.1.2-bin-hadoop2.7.tgz
 
 O próximo passo vai ser descompactar o arquivo que fizemos download:<br>
 !tar xf spark-3.1.2-bin-hadoop2.7.tgz

Por fim podemos instalar o pacote findspark:<br>
!pip install -q findspark

Definir as variáveis.Programas são o Java e o Spark:<br>
import os <br>
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"
os.environ["SPARK_HOME"] = "/content/spark-3.1.2-bin-hadoop2.7"

Variáveis definidas, podemos utilizar o findspark que vai permitir a importação dos pacotes necessários para utilizar o PySpark:<br>
import findspark
findspark.init()

Agora, podemos, por exemplo, importar o SparkSession do módulo pyspark.sql:<br>
from pyspark.sql import SparkSession

Criar sessão Spark, ela vai cuidar de toda a parte de gerenciamento dos nós do processamento em paralelo:<br>
spark = SparkSession.builder \
    .master('local[*]') \
    .appName('Iniciando com Spark') \
    .config('spark.ui.port', '4050') \
    .getOrCreate()
