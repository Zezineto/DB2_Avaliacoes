# Feito por
Fabricio Rodrigues, Fábio Junior, Gabriel Batistuta, Zezineto Mendes, Joao Victor Freitas.

# Introdução
Este repositório contem o trabalho de hadoop feito pelo Docker do grupo SunDB; Ele contem o PDF com a apresentação e os arquivos usados.<br/>
O código para usar o hadoop pelo docker foi baseado no repositorio: https://github.com/big-data-europe/docker-hadoop, que esta contido no repositorio atual.<br/>

Este repositorio tambem possui um arquivo JAR chamado hadoop-mapreduce-examples que não foi usado na apresentação mas foi usado para testar a funcionalidade do hadoop pelo terminal.<br>
Link do repositorio dos arquivos originais do hadoop-mapreduce-examples: https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/

# Sobre o trabalho
Apesar de várias tentativas não foi feito o implemento do código para realizar o "mapreduce" do hadoop com os documentos escolhidos.<br/>
O arquivo "Zips.json" possui uma lista das cidades dos estados unidos contendo o nome, população, coordenadas e sigla do estado. <br/>
Link do arquivo original criado por Simonista: https://gist.github.com/simonista/0c09188c55356b2baa89f90d04644228 <br/>

A ideia a ser implementada seria um "sort", uma organização das cidades a partir da sigla de seu estado, tal organização seria feita com a sigla do estado em ordem alfabética, seguido dos nomes das cidades que lhe pertencem.

EXEMPLO:<br/>
(alabama)<br/>

STATE: AL, CITY: Atmore;<br/>
STATE: AL, CITY: Efaula;<br/>
STATE: AL, CITY: Leeds;<br/>
Etc...<br/>

O arquivo JSON contendo a lista de cidades seria o "Zips.json", <br/>
O arquivo JAR contendo o código criado pelo grupo seria o "json-sort-actual-1.0-SNAPSHOT.jar".<br/>

# Código e execução
Para executar o código foi feito uma inicialização do terminal usando a pasta docker-hadoop (pelo terminal do windows nesse caso), no qual foram aplicados os seguintes inputs:<br/>
para iniciar o docker:
```
  docker-compose up -d
```
Para inserir os arquivos a serem lidos pelo terminal linux dentro do docker foram feitos os seguintes comandos:
```
  docker cp zips.json namenode:/tmp
  docker cp json-sort-actual-1.0-SNAPSHOT namenode:/tmp
```
Agora para usar o terminal linux contido no docker e preparar os arquivos para o teste do mapreduce
```
  # docker exec -it namenode bash
  # hdfs dfs -mkdir -p /user/root
  # hdfs dfs -mkdir -p /user/root/input
  # cd tmp
  tmp# hdfs dfs -put zips.json /user/root/input
```
Para testar o código feito chamamos sua "função" `JsonSortingJob`, que usa o arquvio json contigo no diretorio input como base

```
  hadoop jar json-sort-actual-1.0-SNAPSHOT.jar JsonSortingJob input output
```
Apos isso o código sera rodado e sera criado um diretorio outpout que não contem nenhum arquivo, isto pode ser visto rodando
```
  tmp# hdfs dfs -ls /user/root
```
No fim de tudo para desativar o docker basta rodar o seguinte
```
  tmp# exit
  docker-compose down
```
