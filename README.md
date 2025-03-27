# Ponderada Tradução Automática e o Conjunto de Dados

## 9.5.7. Exercícios

**Tente valores diferentes do argumento num_examples na funçãoload_data_nmt. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?**

Ao testar diferentes valores para o parâmetro num_examples na função load_data_nmt, ficou bem claro como isso afeta diretamente o tamanho dos vocabulários de origem e destino. Quando deixei o valor padrão de 600, os vocabulários ficaram maiores, e os índices nos tensores X e Y chegaram a valores bem altos, como 100, 166 ou até 171. Isso mostra que mais palavras foram incluídas no vocabulário, o que faz sentido, já que com mais frases processadas, mais palavras únicas aparecem no conjunto de dados.

Quando reduzi o num_examples para 60, os índices ficaram muito mais baixos, como 29, 12 ou até 0. Ou seja, menos palavras passaram a fazer parte do vocabulário porque menos exemplos foram usados para construí-lo. Depois, aumentei um pouco para 200 no num_examples, e foi possível perceber que houve um aumento, mas não chegou a uma quantidade bem alta de palavras únicas em comparação de quando o num_examples era 600.
Isso confirma que o tamanho do vocabulário depende bastante da quantidade de exemplos que você usa como base, e que usar um número muito pequeno de frases limita bastante a diversidade de palavras para o modelo aprender.

**O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?**

Acredito não ser uma boa ideia usar essa abordagem nesses casos. Isso porque esses idiomas não usam espaço entre palavras, então se a tentarmos fazer a divisão só com base nisso, vai acabar gerando tokens quebrados, errados ou misturados. Para lidar com isso, o ideal é usar tokenização por caractere, subpalavra ou ferramentas específicas para cada idioma, como o jieba para chinês ou o MeCab para japonês. Essas abordagens são muito mais eficazes, porque entendem melhor a estrutura linguística desses idiomas e ajudam o modelo a aprender com mais qualidade.
