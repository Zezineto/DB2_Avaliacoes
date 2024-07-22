Este repositório contem o trabalho de hadoop feito pelo Docker do grupo SunDB.
Apesar de várias tentativas não foi feito o implemento do código para realizar o "mapreduce" do hadoop com os documentos escolhidos.
O arquivo "Zips.json" possui uma lista das cidades dos estados unidos contendo o nome, população, coordenadas e sigla do estado, a ideia a ser implementada seria um "sort", uma organização das cidades a partir da sigla de seu estado, tal organização seria feita com a sigla do estado em ordem alfabética, seguido dos nomes das cidades que lhe pertencem.

EXEMPLO:
(alabama)
STATE: AL, CITY: Atmore;
STATE: AL, CITY: Efaula;
STATE: AL, CITY: Leeds;
Etc...

O arquivo JSON contendo a lista de cidades seria o "Zips.json",
O arquivo JAR contendo o código criado pelo grupo seria o "json-sort-actual-1.0-SNAPSHOT.jar".