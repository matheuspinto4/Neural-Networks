2.1                                                     INTRODUÇAO

A propriedade que eh de importancia primordial para uma rede neural eh a sua habilidade de aprender a partir de seu ambiente e
de melhorar o seu desempenho atraves da parendizagem. A melhoria do desempenho ocorre com o tempo de acordo com alguma medida
preestabelecida. Uma rede neural aprende acerca do seu ambiente atraves de um processo interativo de ajustes aplicados a seus
pesos sinapticos e niveis de bias. Idealmete, a rede se torna mais instruida sobre seu ambiente apos cada iteraçao do processo
de aprendizagem.
Ha atividades demais associadas `a noçao de "aprendizagem" para justificar a sua definiçao de forma precisa. Alem disso, o
processo de aprendizagem depende do ponto de vista, o que causa dificuldade em se obter um consenso sobre uma definiçao precisa
do termo. Reconhecendo que nosso interesse particular se concentra nas redes neurais, utilizamos uma definiçao de aprendizagem
que eh adaptada de Mendel e McClaren(1970).
    Definimos aprendizagem no contexto de redes neurais como:

> Aprendizagem eh um processo pelo qual os parametros livres de uma rede neural sao adaptados atraves de um processo de estimulaçao pelo ambiento no qual a rede esta inserida. O tipo de aprendizagem eh determinado pela maneira pela qual a modificaçao dos parametros ocorre.

Esta definiçao do processo de aprendizagem implica a seguinte sequencia de eventos:

1. A rede neural eh estimulada por um ambiente
2. A rede neural sofre modificaçoes nos seu parametros livres como resultado desta estimulaçao
3. A rede neural ressponde de uma maneira nova ao ambiente, devido `as modificaçoes ocorridas na sua estrutura interna.

    Um conjunto preestabelecido de regras bem0definidas para a soluçao de um problema de aprendizagem eh denominado um
algoritimo de aprendizagem. Como se pode esperar, nao ha um algoritimo de aprendizagem unico para o projeto de redes neurais.
Em vez disso, temos um "conjunto de ferramentas" representado por uma variante de algoritmos de aprndizagem, cada qual
oferecendo vantagens especificas. Basicamente, os algoritimos de aprendizagem diferem entre si pela forma como eh formulado o
ajuste de um peso sinaptico de um neuronio. Um outro fator a ser considerado eh a maneira pela qual uma rede neural (maquina de
aprendizagem), constituida de um conjunto de neuronios interligados, se relaciona com o seu ambiente. Neste ultimo contexto,
falamos de um parasigma de aprendizagem que se refere a um modelo do ambiente no qual a rede neural opera.




2.2                                          APRENDIZAGEM POR CORREÇAO DE ERRO

Para ilustrar nossa primeira regra de aprendizagem, considere o caso simples de um neuronio k que constitui o unico no
computacional da camada de saida de uma rede neural alimentada adiante, como representado pela figura 2.1a. O neuronio k eh
acionado por um vetor de sinal X(n) produzido por uma ou mais camadas de neuronios ocultos, que sao, por sua vez, acionadas por
um vetor de entrada (estimulo) aplicado aos nos de fonte (i.e., a camada de entrada) da rede neural. O argumento n representa o
instante de tempo discreto, ou mais precisamente, o passo de tempo de um processo iterativo envolvido no ajuste dos pesos
sinapticos d neuronio k. O sinal de saida do neuronio k eh representado por Yk(n). Este sinal de saida, representando a unica
saida da rede neural, eh comparado com uma resposat desejada ou saida-alvo, representada por Dk(n). Consequentemente, eh
produzido um sinal de erro, representado por Ek(n). Por definiçao, temos assim

                    Ek(n) = Dk(n) - Yk(n)   (Eq. 2.1)

O sinal de erro Ek(n) aciona um mecanismo de controle, cujo proposito eh aplicar uma sequencia de ajustes corretivos aos pesos
sinapticos do neuronio k. Os ajustes corretivos sao projetados para aproximar passo a passo o sinal de saida Yk(n) da resposta
desejada Dk(n). Este objetivo eh alcançado minimizando-se uma funçao de custo ou indice de desempenho, &(n), definido em termos
do sinal de erro Ek(n) como:

                    &(n) = (Ek(n)^2)/2    (Eq. 2.2)

Com isso, &(n) eh o valor instantaneo da energia do erro. Os ajustes passo a passo dos pesos sinapticos do neuronio k continuam
ate o sistema atingit um estado estavel (i.e., os pesos sinapticos estao essencialmente estabilizados). Neste ponto, o processo
eh encerrado.
    O processo de aprendizagem descrito aqui eh denominado, por razoes obvias, aprendizagem por correçao de erro. Em
particular, a minimizaçao da funçao  de custo &(n) resulta na regra de aprendizagem normalmente referida como regra delta ou
regra Windrow-Hoff, assim denominada em homenagem aos seu criadores. Suponha que Wkj(n) represente o valor do peso sinaptico
Wkj do neuronio k excitado por um elemnto Xj(n) do vetor de sinal X(n) no passo de tempo n eh definido por

                    DELTA(Wkj(n)) = N * Ek(n)*Xj(n)    (Eq. 2.3)

onde N eh uma constante positiva que determina a taxa de aprendizado quando avançamos em um passo no processo de aprendizagem.
Eh, portanto, natural que denominemos N parametro taxa de aprendizado. Em outras palavras, a regra delta pode ser formulada
como:

                O ajuste feito e um peso sinaptico de um neuronio eh proporcional ao produto do sinal de erro pelo
                sinal de entrada da sinapse em questao.

Note-se que a regra delta, assim formulada, pressupoe que o sinal de erro seja diretamente mensuravel. Para que esta mediad
seja assim realizavel, necessitamos calramente de que a resposta desejada seja fornecida por alguma fonte externa, que seja
diretamente acessivel ao neuronio k. Em outras palavras, o neuronio k eh visivel ao mundo externo. Da fugura 2.1a, percebemos
que a aprendizagem por correçao de erro tem natureza local. Isto apenas significa que os ajustes sinapticos feitos pela regra
delta sao localizados em torno do neuronio k.
    Tendo calculado o ajuste sinaptico DELTA(Wkj(n)), o valor atualizado do peso naptico Wkj eh determinado por

                Wkj(n+1) = Wkj(n) + DELTA(Wkj(n)) (Eq. 2.4)

Na verdade, esses valores podem ser vistos como os valores novo e antigo do peso Wkj , respectivamente. Em termos
computacionais, podemos escrever

            Wkj(n) = Z^(-1)[Wkj(n+1)]  (Eq. 2.5)

onde Z^(-1)[] eh o operados atraso unitario. Isto eh, Z^(-1)[] representa um elemento de armazenamento.
    A figura 2.1b mostra uma representaça em grafo de fluxo de sinal do processo de aprendizagem por erro, enfocando a
ativadade na vizinhança do neuronio k. Vemos que a aprendizagem por correçao de erro eh um exemplo de um sistema realimentado
de laço fechado. Da teoria de controle sabemos que a estabilidade de um sistema como esse eh determinada pelos parametros que
constituem os laços de realimentaçao do sistema. No caso temos apenas um laço de realimentaçao, e um desses parametros, que eh
particularmente interessante, eh o parametro de taxa de aprendizado N. Por esse motivo, eh importante que N seja selecioando
cuidadosamente, para assegurar que seja alcançada a estabilidade ou convergencia do processo de aprendizagem iterativo. A
escolha de N tem tambem uma influencia profunda na precisao e em outros aspectos do processo de aprendizagem. Em resumo, o
parametro de taza de aprendizado N desempenha na pratica um papel-chave, determinando o desempenho da aprendizagem por correçao
de erro.



2.3                                         APRENDIZAGEM BASEADA EM MEMORIA

Na aprendizagem baseada em memoria, todas as (ou a maioria delas) experiencias passadas sao armazenadas explicitamente em uma
grande memoria de exemplos de entrada-saida classificados corretamente {(Xi,Di)}[1,N], onde Xi representa um vetor de entrada e
Di representa a resposta desejada correspondente. Sem perda de generalidade, restringimos a resposta desejada a ser um escalar.
Em um problema de classificaçao de padroes binarios, por exemplo, ha duas classes/hipotese a serem consideradas, representadas
por $1 e $2. Neste exemplo, a resposat desejada Di assume o valor 0 (ou -1) para a classe $1 e o valor 1 para a classe $2.
Quando desejamos classificar um vetor de teste Xteste (nao visto antes), o algoritmo responde buscando e analisando os dados de
treinamento em uma "vizinhança local" de Xteste.
    Todos os algoritmos de aprendizagem baseada em memoria envolvem dois ingredientes essencias:

        * O criterio utilizado para definir a vizinhança de teste Xteste.
        * A regra de aorendizagem aplicada aos exemplos de treinamento na vizinhança local de Xteste.

Os algoritmos diferem entre si na forma como estes dois ingredientes sao definidos.
    Em um tipo simples mais efetivo de aprendizagem baseada em memoria conhecido como a regra do vizinho mais proximo, a
vizinhança local eh definida como exemplo de treinamento que se encontra na vizinhança imediata do vetor de teste Xteste. Em
particular, dizemos que o veotor

            X`N e {x1,x2,...,xN}  (2.6)

eh o vizinho mais proximo de Xteste se

            min d(Xi, Xteste)[i] = d(X`N, Xteste)   (2.7)

onde d(Xi, Xteste) eh a distancia euclidiana entre os vetores Xi e Xteste. A classe associada a distancia minima, ou seja, o
vetor X`N eh apresentada como a classificaçao de Xteste. Esta regra eh independente da distribuiçao fundamental responsavel
pela geraçao dos exemplos de treinamento.
    Cover e Hart (1967) estudaram formalmente a regra do vizinho mais proximo como uma ferramenta para classificaçao de
padroes. A analise apresentada por eles eh baseada em duas suposiçoes:

    * Os exemplos classificados (Xi, Di) sao independentemente e idendicamente distribuidos (iid),
      de acordo com a distribuiçao de probabilidade conjunta do exemplo (x,d).
    * O tamanho da amostra N eh infinitamente grande.

Levando em consideraçao estas duas suposiçoes, mostra-se que a probabilidade de erro de classificaçao pela regra do vizinho
mais proximo eh limitada acima pelo dobro da probabilidade de erro bayesiana, isto eh, a minima probabilidade de erro entre
todas as regras de decisao. A probabilidade de erro bayesiana sera discutida ainda. Neste sentido, pode-se dizer que metade da
informaçao sobre a classificaçao de um conjunto de treinamento de tamanho inifinito esta contida no vizinho mais proximo, o que
eh um resultado supreendente.
    Uma variante do classificador pelo vizinho mais proximo eh o classificados pelos k vizinhos mais proximos, qu eprocede como
segue:

    * identifique os k padroes classificados que se encontram mais proximos do vetor de teste Xteste, para um numero inteiro k.
    * atribua Xteste `a classe (hipotese) que esta mais frequentemente representada nos k vizinhos mais proximos de Xteste
      (i.e., use uma votaçao majoritaria para fazer a classificaçao).
Assim, o classificador pelos k vizinhos mais proximos atua como um dispositivo que calcula a media. Em particular, ele
discrimina um dado estranho, como ilustrado na figura 2.2 para k = 3. Um dado estranho eh uma observaçao qu etem um valor
improvavel em relaçao a um modelo de interesse.



2.4                                                APRENDIZAGEM HEBBIANA

O postulado de aprendizado de Hebb eh a mais antiga e mais famosa de todas as regras de aprendizagem; ele eh assim denominado
em homenagem ao neuropsicologo Hebb(1949). Citando o livro de Hebb (1948, p.62). The Organization of Behavior.

        Quando um axionio da celula A esta perto o suficiente para excitar uma celula B e participa do seu
        disparo repetida ou persistentemente, entao algum proceso de crescimento ou modificaçao metabolica
        acontece em uma das celulas ou em ambas, de tal forma que a eficiencia de A como uma das celulas
        que dispara B eh aumentada.

Hebb propos esta modificaçao como base da aprendizagem associativa (a nivel celular), que resultaria em uma modificaçao
permanete do padrao de atividade de um "agrupamento de celulas nervosas" espacialmente distribuido.
    Esta afirmaçao foi feita em um contexto neurobiologico. Podemos expandir e reescreve-lo como uma regra em duas partes:

1. Se dois neuronios em ambos os lados de uma sinapse (conexao) sao ativados simultaneamente (i.e, sincronamente), entao a
força daquela sinapse eh seletivamente aumentada.
2. Se dois neuronios em ambos os lados de uma sinapse sao ativados assincronamente, entao aquela sinapse eh seletivamente
enfraquecida ou eliminada.

Uma sinapse assim eh denominada uma sinapse Hebbiane. (A regra de Hebb original nao contem a parte 2.). Mais precisamente,
definimos uma sinapse hebbiana como uma sinapse que usa um mecanismo dependente do tempo, altamente local e fortemente
interativo para aumentar a eficiencia sinaptica como uma funçao da correlaçao entre as atividades pre-sinaptica e
pos-sinaptica. A partir desta definiçao podemos deduzir os seguintes quatro mecanismos (propriedades) fundamentais que
caracterizam uma sinapse hebbiana:

1.Mecanismo_dependente_do_tempo. Este mecanismo se refere ao fato de que as modificaçoes em uma sinapse hebbiana dependem do
tempo exato de ocorrencia dos sinais pre-sinapticos e pos-sinapticos.
2.Mecanismo_local. Pela sua natureza, uma sinapse eh um local de transmissao onde sinais portadores de informaçao
(representandos a atividade incidente nas unidades pre-sinaptica e pos-sinaptica) estao em contiguidade espaço-temporal. Esta
informaçao localmente disponivel eh utilizada por uma sinapse hebbiana para produzir uma modificaçao sinaptica local que eh
especifica para a entrada.
3.Mecanismo_interativo. A ocorrencia de uma modificaçao em uma sinapse hebbiana depende dos sinais em ambos os lados da
sinapse. Isto eh, uma forma de aprendizagem hebbiana depende de uma "interaçao verdadeira" entre os sinais pre-sinapticos e
pos-sinapaticos, no sentido de que nao podemos fazer uma previsao a partir de apenas uma dessas duas atividades. Note tambem
que esta dependecia ou interaçao pode ser de natureza deterministica ou estatistica.
4.Mecanismo_conjuncional_ou_correlativo. Uma interpretaçao do postulado de aprendizado de Hebb eh que a condiçao para uma
modificaçao a eficiencia sinaptica eh a conjunçao dos sinais pre-sinaptico e pos-sinaptico. Assim, de acordo com esta
interpretaçao, s ocorrencia simultanea dos sinais pre-sinapticos e pos-sinapticos (dentro de um curto intervalo de tempo) eh
sufciente para produzir a modificaçao sinaptica. Eh por esta razao que uma sinapse hebbiana eh algumas vezes denominada sinapse
conjuncional. Para uma outra interpretaçao do postulado de aprendizado de Hebb, podemos considerar o mecanismo interativo que
caracteriza uma sinapse hebbiana em termos estatisticos. Em particular, a correlaçao temporal entre os sinais pre-sinaptico e
pos-sinaptico eh vista como sendo responsavel por uma modificaçao sinaptica. Nest esentido, uma sinapse hebbiana eh tambem
denominada sinapse correlativa. A correlaçao eh de fato a base do aprendizado.


    # REFORÇO E DEPRESSAO SINAPTICOS///

A definiçao de uma sinapse hebbiana apresentada aqui nao inclui processos adicionais que podem resultar no enfraquecimento de
uma sinapse conectando um par de neuronios. De fato, podemos generalizar o conceito de uma modificaçao hebbiana reconhecendo
que uma atividade positivamente correlacioanda produz reforço sinaptico e que uma atividade nao-correlacionada ou negativamente
correlacionada produz enfraquecimento sinaptico. A depressao sinaptica pode ser tambem nao-interativo. Especificamente, a
condiçao interativa para o enfraquecimento sinaptico pode ser simplesmente a atividade nao-coincidente pre-sinaptica ou
pos-sinaptica.
    Podemos seguir um passo `a frente, classificando uma modificaçao sinaptica como hebbiana, anti-hebbiana e nao-hebbiana. De
acordo com este esquema, uma sinapse hebbiana aumenta sua força quando estes sinais pre-sinaptico e pos-sinapticos
positivamente correlacionados e diminui a sua força quando estes sinais nao sao correlacionados ou sao negativamente
correlacioandos. Inversamente, uma sinapse anti-hebbiana, enfraquece sinais pre-sninapticos e pos-sinapticos correlacionados e
reforça sinais negativamente correlacioandos. Tanto em uma sinapse hebbiana como em uma sinapse anti-hebbiana, entretanto, a
modificaçao da eficiencia sinaptica se baseia em um mecanismo que eh dependente do tempo, altamente local e de natureza
fortemente interativa. Neste sentido, uma sinapse anti-hebbiana eh ainda de natureza hebbiana, apesar de nao o ser
funcionalmente. Uma sinapse nao-hebbiana, por outro lado, nao envolve qualquer tipo de mecanismo hebbiano.

    MODELOS MATEMATICOS DE MODIFICAÇOES HEBBIANAS

Para formular a aprendizagem hebbiana em termos matematicos, considere um peso sinaptico Wkj do neuronio k com sinais
pre-sinaptico e pos-sinaptico representados por Xj e Yk, repectivamente. O ajuste aplicado ao peso sinaptico Wkj no passo de
tempo n eh expresso na forma generalizar

                        DELTA(Wkj(n)) = F(Yk(n), Xj(n))    (Eq 2.8)

onde F(.,.) eh uma funçao tanto do sinal pre-sinaptico como do pos-sinaptico. Os sinais Xj(n) e Yk(n) sao frequentemente
tratados como adimencionais. A formula da equaçao (2.8) admite muitas formas, sendo que todas sao qualificadas como hebbianas.
A seguir, consideremos duas destas formulas.

1.HIPOTESE_DE_HEBB. A forma mais simples de aprendizado hebbiana eh descrita por

                        DELTA(Wkj(n)) = N*Yk(n)*Xj(n)     (Eq 2.9)

onde N eh uma constante postitiva que determina a taxa de aprendizagem. A equaçao (2.9) claramente enfatiza a natureza
correlativa de uma sinapse hebbiana. Ela eh algumas vezes referida como a regra do produto das atividades. A curva superior da
figura 2.3 mostra uma representaçao grafica da equaçao (2.9), com a modificaçao DELTA(Wkj) traçada em funçao do sinal de saida
(atividade pos-sinaptica) Yk. Desta representaçao, vemos que a aplicaçao repetida do sinal de entrada (ativiadde pre-sinaptica)
Xj resulta em um aumento de Yk e , portanto, em um crescimento exponencial que ao final leba a conexao sinaptica `a saturaçao.
Naquele ponto nenhuma informaçao sera armazenada na sinapse e a seletividade eh perdida.


2.HIPOTESE_DE_COVARIANCIA. Uma forma de superar a limitaçao da hipotese de Hebb eh atraves da utilizaçao da hipotese da
covariancia introduzida por Seknowski. Nesta hipotese, os sinais pre-sinapticos e pos-sinapticos na equaçao (2.9) sao
substituidos pelos desvios dos sinais pre-sinaptico e pos-sinapticos em relaçao aos seus respectivos valores medios em um certo
intervalo de tempo. Considere que Xmed e Ymed sejam os valores medios no tempo dos sinais pre-sinapticos e pos-sinapticos,
respectivamente. De acordo com a hipotese de covariancia, o ajuste aplicado ao peso sinaptico Wkj eh definido por

                        DELTA(Wkj(n)) = N*(Yk(n) - Ymed)*(Xj(n) - Xmed)(Eq 2.10)

onde N eh o parametro taxa de aprendizado. Os valores medios Xmed e Ymed constituem os limiares pre-sinaptico e pos-sinaptico,
que determinam o sinal da modificaçao sinaptica. Em particular, a hipotese da covariancia permite o seguinte:
    * A convergencia para um estado nao-trivial, que eh alcançado quando Xk = Xmed ou Yj - Ymed.
    * A previsao da potenciaçao sinaptica (i.e., aumento da força sinaptica) e a depressao sinaptica (i.e., diminuiçao da força
      sinaptica).

A figura 2.3 ilustra a diferença entre a hipotese hebbiana e a hipotese da covariancia. Em ambos os casos, DELTA(Wkj) depende
linearmente de Yk; entretanto, o cruzamento com o eixo de Yk na hipotese de Hebb ocorre na origem, enquanto que na hipotese da
covariancia ela ocorre em Yk = Ymed.
    Podemos fazer as seguintes observaçoes importantes sobre a equaçao (2.10):

1. O peso sinaptico Wkj eh reforçado se houver niveis suficientes de atividades pre-sinapticas e pos-sinapticas, ou seja, se
   ambas as condiçoes Xj > Xmed e Yk > Ymed forem satisfeitas.
2. O peso sinaptico eh deprimido se ocorrer umas das seguintes situaçoes:

    * uma ativaçao pre-sinaptica (i.e.m Xj > Xmed) na ausencia de ativaçao pos-sinaptica suficiente (i.e., Yk < Ymed).
    * uma ativaçao pos-sinaptica (i.e.m Yj > Ymed) na ausencia de ativaçao pre-sinaptica suficiente (i.e., Xk < Xmed).

Este comportamento pode ser visto como uma forma de competiçao temporall entre os padroes incidentes.
    Ha uma forte evidencia fisiologica para a aprendizagem hebbiana na area do cerebro chamada hipocampo. O hipocampo
desempenha um papel importante em certos aspecors de aprendizagem e memoria. Esta evidencia fisiologica torna a aprendizagem
hebbiana bastante atrativa.



2.5                                             APRENDIZAGEM COMPETITIVA

Na aprendizagem competitiva, como o nome implica, os neuronios de saida de uma rede neural competem entre si para se tornar
ativos (disparar). Enquanto que em uma rede neural baseada na aprendizagem hebbiana, varios neuronios de saida podem estar
ativos simultaneamente, na aprendizagem competitiva omente um unico neuronio de saida esta ativo em um determinao instante. Eh
essa caracteristica que torna a aprendizagem competitva muito adequada para classificar um conjunto de padroes de entrada.
    Existem tres elementos basicos em uma regra de aprendizagem competitiva:

    * Um conjunto de neuronios que sao todos iguais entre si, exceto por alguns pesos sinapticos distribuidos aleatoriamente, e
      que por isso respondem diferentemente a um dado conjunto de padroes de entrada.
    * Um limite imposto sobre a "força" de cada neuronio.
    * Um mecanismo que permite qu eo neuronio compita pelo direito de responder a um dado subconjunto de entradas, de forma que
      somente um neuronio de saida, ou somente um neuronio por grupo esteja ativo (i.e., "ligado") em um determinado instante.
      O neuronio que vence a competiçao eh denominado um neuronio vencedor leva tudo.

Correspondentemente, os neuronios individuais da rede aprendem a se especializar em agrupamentos de padroes similares; fazendo
isso, eles se tornam detectores de caracteristicas para classes diferentes de padroes de entrada.
     Na forma mais simples de aprendizagem comeptitiva, a rede neural tem uma unica camada de neuronios de saida,estando cada
neuronio totalmente conectadoaos nos de entrada. A rede pode incluir conexoes de realimentaçao entre os neuronios, como
indicado na figura 2.4. Na arquitetura aqui descrita, as conexoes de realimentaçao realizam inibiçao lateral, com cada neuronio
tendendo a inibir o neuronio ao qual esta lateralmente conectado. Por outro lado, as conexoes einapticas de alimentaçao adiante
na rede da Fig. 2.4 sao todas excitadoras.
    Para um neuronio k ser o neuronio vencedor, seu campo local induzido Vk para um padrao de entrada especificado x deve ser
maior entre todos os neuronios da rede. O sinal de saida Yk do neuronio vencedor k eh colocado em um; Os sinais de saida de
todos os neuronios que perdem a competiçao sao colocados em zero. Com isso, podemos escrever

                                           / 1 se Vk >Vj para todos os j
                                    Yk  = |
                                           \ 0 caso o contrario

onde o campo local induzido Vk representa a açao combinada de todas as entradas diretas e realimentadas do neuronio k.
    Considere que Wkj represente o peso sinaptico conectando o no de entrada j ao neuronio k. Suponha que a cada neuronio seja
alocada uma quantidade fixa de peso sinaptico (i.e., todos os pesos sinapticos sao positivos), que eh distribuida entre seus
nos de entrada; ou seja,

                                    SUM(Wkj) = 0 para todo k

Um neuronio, entao, aprende ao deslocar pesos sinapticos de seus nos de entrada inativos para os seus nos ativos. Se um
neuronio nao responde a um padrao de entrada particular, entao cada no de entrada deste neuronio libera uma certa proporçao de
seu peso sinaptico e este peso liberado sera entao distribuido uniformemente entre os nos de entrada ativos. De acordo com a
regra de aprendizagem competitiva padrao, a variaçao DELTA(Wkj) eh definida por

                                                  / N(Xj - Wkj) se o neuronio k vencer a competiçao
                                    DELTA(Wkj) = |
                                                  \ 0 se o neuronio k perder a competiçao

onde N eh o parametro taxa de aprendizagem. Esta regra tem o efeito global de mover o vetor de peso sinaptico Wk do neuronio
vencedor k em direçao ao padrao de entrada x.
    Podemos utilizar a analogia geometrica representada na Fig. 2.5 para ilustrar a essencia da aprendizagem competitiva.
Supomos que cada padrao (vetor) de entrada x tem um determinado comprimento euclidiano constante, de forma que podemos ve-lo
como um ponto em uma esfera unitaria N-dimensional, onde N eh o numero de nos de entrada. N representa tambem a dimensao de
cada vetor de peso sinaptico Wk. Supomos ainda que todos os neuronios da rede tem o mesmo comprimento euclidiano (norma), como
mostrado por

                                    SUM(Wkj ^ 2) = 1 para todo k

Quando os pesos sinapticos sao escalonados adequadamente, formam um conjunto de vetores que se encontram na mesma esfera
unitaria N-dimensional. Na figura 2.5a, mostramos tres agrupamentos (clusters) naturais dos padroes de estimulo representados
por pontos. Esta figura inclui tambem um estado inicial possivel para a rede (representados por cruzes) que pode existir antes
do aprendizado. A Figura 2.5b mostra um estado final tipico da rede que resulta da utiliaçao da aprendizagem competitiva. Em
particular, cada neuronio de saida descobriu um agrupamento de padroes de entrada movendo o seu veotr de peso sinaptico apra o
centro de gravidade do agrupamento descoberto. Esta figura ilustra a habilidade de uma rede neural de realizar a tarefa de
agrupamentos (clustering) atraves de aprendizagem competitiva. Entretanto, para realizar esta funçao de uma maneira "estavel",
os padroes de entrada devem se localizar em agrupamentos suficientemente distintos. Caso contrario, a rede pode ser instavel
porque nao repondera mais a um determinado padrao de entrada com o mesmo neuronio de saida.


2.6                                             APRENDIZAGEM DE BOLTZMANN

A regra de aprendizagem de boltzmann eh um algoritimo de aprendizagem estocastico derivado de ideias enraizadas na mecanica
estatistica. Uma rede neural projetada com base na regra de aprendizagem de Boltzmann eh denominada uma maquina de Boltzmann.
    Em uma maquina de Boltzmann, os neuronios constituem uma estrutura recorrente e operam de  uma maneira binaria, uma vez
que, por exemplo, eles estao ou em um estado "ligado" representado por +1, ou em um estado "desligado" representado por -1. A
maquina eh caracterizada por uma funçao de energia, E, cujo valor eh determinado pelos estados particulares ocupados pelos
neuronios individuais da maquina, como motrado por

                                E = -1/2 * SUM(SUM(Ekj*Xj*Xk)[k])[j]  , onde j != k                            (Eq 2.15)

onde Xj eh o estado do neuronio j e Wkj o peso sinaptico conectando o neuronio j ao neuronio k. O fato de que j != k significa
apenas que nenhum dos neuronios da maquina tem auto-realimentaçao. A maquina opera escolhendo um neuronio ao acaso - por
exemplo, o neuronio k - em um determinado passo do processo de aprendizagem, trocando entao o estado do neuronio k do estado Xk
para o estado -Xk a uma temperatura T com probabilidade

                                P(Xk -> -Xk) = 1/(1 + exp(-DELTA(Ek)/T))

onde DELTA(Ek) eh a variaçao de energia (i.e., variaçao da funçao de energia da maquina) resultante daquela troca. Note que T
nao eh uma temperatura fisica, mas apenas uma pseudotemperatura. Se esta regra for aplicada repetidamente, a maquina atingira o
equilibrio termico.
    Os neuronios de uma maquina de Boltzmann se dividem em dois grupos funcionais: o svisiveis e os ocultos. Os neuronios
visiveis fornecem uma interface entre a rede e o ambiente em que ela opera, enquanto que o sneuronios ocultos sempre operam
livremente. Ha dois modos de operaçao a serem considerados:

  * 1.Condiçao_presa, na qual os neuronios visiveis estao todos presos a estados especificos determinados pelo ambiente.
  * 2.Condiçao_de_operaçao_livre, na qual todos os neuronios (visiveis e ocultos) podem oerar livremente.

Suponha que Pkj+ represente a correlaçao entre os estados dos neuronios j e k, com a rede na sua condiçao presa. Suponha que
Pkj- represente a correlaçao entre os estados dos neuronios j e k, com a rede na sua condiçao de operaçao livre. Ambas as
correlaçoes correspondem as medias sobre todos os estados possiveis da maquina, quando ela esta em equilibrio termico. Entao,
de acordo com a regra de aprendizagem de Boltzmann, a variaçao DELTA(Wkj) aplicada ao peso sinaptico Wkj do neuronio j para o
neuronio k eh definida por

                                DELTA(Wkj) = N( (pkj+) - (pkj-) ), j != k
onde N eh o parametro taxa de aprendizagem. Note qie tanto Pkj+ quanto Pkj- assumem valores no intervalo -1 e +1.



2.7                                      O PROBLEMA DE ATRIBUIÇAO DE CREDITO

Quando se estudam algoritmos de aprendizagem para sistemas distribuidos, eh util se considerear a noçao de atribuiçao de
credito. Basicamente, o problema de atribuiçao de credito eh problema de se atribuir credito ou culpa por resultados globais a
cada uma das decisoes internas que tenham sido tomadas por uma maquina de aprendizagem e que tenham contribuido para aqueles
resultados. (O problema de atribuiçao de credito eh tambem denominado problema de carga, isto eh, o problema de "carregar" um
determinado conjunto de dados de treinamento para dentro dos parametros livres da rede.)
    Em muitos casos, a dependencia dos resultados em relaçao a decisoes internas eh mediada por uma sequencia de açoes tomadas
pela maquina de aprendizagem. Em outras palavras, as decispes internas afetam a escolha das açoes particulares que sao tomadas
e, com isso, as açoes e nao as decisoes internas influenciam diretamente os resultados globais. Nestas situaçoes, podemos
decompor o problema de atribuiçao de credito em dois subproblemas:

    1.A_atribuiçao_de_credito_por_resultados_a_açoes. Este eh o chamdo problema de atribuiçao de credito temporal que envolve
os instantes de tempo quando as açoes que merecem credito foram realmente tomadas.
    2.A_atribuiçao_de_credito_por_açoes_a_decisoes_internas. Este eh o chamado problema de atribuiçao de credito estrutural que
envolve atribuir credito as estruturas internas das açoes geradas pelo sistema.

O problema de atribuiçao de credito estrutural eh relevante no contexto de uma maquina de aprendizagem com multiplos
componentes quando devemos determinar precisamente qual componente particular do sistema deve ter seu comportamento alterado e
em que medida, de forma a melhorar o desempenho global do sistema. Por outro lado, o problema de atribuiçao de credito temporal
eh relevante quando ha muitas açoes tomadas por uma maquina de aprendizagem que acarretam certos resultados, e devemos
determinar quais açoes foram responsaveis pelos resultados. O problema combinado de atribuiçao de credito temporal e estrutural
eh enfrentado por qualquer maquina de aprendizagem distribuida que se esforce em melhorar seu desempenho em situaçoes
envolvendo comportamento estendido no tempo.
    O problema de atribuiçao de credito surge, por exemplo, quando a aprendizagem de correçao de erro eh aplicada em uma rede
neural de multiplas camadas alimentada adiante. A operaçao de cada neuronio oculto, bem como de cada neuronio de saida desta
rede, eh importante para a correta operaçao global da rede, em uma tarefa de aprendizagem de interesse. Ou seja, para resolver
uma tarefa predeterminada, a rede deve atribuir certas formas de comportamento a todos os seus neuronios, atraves da
especificaçao da aprendizagem por correçao de erro. Tendo em mente esta fundamentaçao, considere a situaçao descrita na Fig.
2.1a. Como o neuronio de saida k eh visivel para o mundo externo, eh possivel fornecer uma resposta desejada para este
neuronio. No que diz respeito ai neuronio de saida, pode-se ajustar diretamente os pesos sinapticos deste neuronio de acordo
com a aprendizagem por correçao de erro, como esboçado na Seçao 2.2. Mas como devemos atribuir credito ou culpa pela açao dos
neuronios ocultos quando o processo de aprendizagem por correçao de erro eh utilizado para ajustar os respectivos pesos
sinapticos desses neuronios: A resposata para a questao fundamental requer atençai mais detalhada; ela eh apresentada no
capitulo 4, onde sao descritos os detalhes algoritmicos do projeto de redes neurais de multiplas camadas alimentadas adiante.


2.8                                               APRENDIZAGEM COM UM PROFESSOR

Voltamos agora nossa atençao para os paradigmas de aprendizagem. Começamos considerando a aprendizagem com um professor, que eh
tambem denominada aprendizagem supervisionada. A figura 2.6 mostra um diagrama em blocos que ilustra esta forma de
aprendizagem. Em termos conceituais, podemos considerar o professor como tendo conhecimento sobre o ambiente, com este
conhecimento sendo representado por um conjunto de exemplos de entrada-saida. Entretanto, o ambiente eh desconhecido pela rede
neural de interesse. Suponha agora que o professor e a rede neural sejam expostos a um vetor de treinamento (i.e, exemplo)
retirado do ambiente. Em virtude de seu conehcimento previo, o professor eh capaz de fornecer `a rede neural uma resposta
desejada para aquele vetor de treinamento. Na verdade, a resposta desejada representa a açao otima a ser realizada pela rede
neural. Os parametros da rede sao ajustados sob a influencia combinada do vetor de treinamento e do sinal de erro. O sinal de
erro eh definido como a  diferença entre a resposta desejada e a resposta real da rede. Este ajuste eh realizado passo a passo,
iterativamente,com o objetivo de fazer a rede neural emular o professor; supoe-se que a emulaçao seja otima em um sentido
estatistico. Desta forma, o conhecimento do ambiente disponivel ao professor eh transferido para a rede neural atraves de
treinamento, da forma mais completa possivel. Quando esta condiçao eh alcançada, podems entao dispensar o professor e deixar a
rede neural lidar com o ambiente inteiramente por si mesma.
    A aprendizagem supervisioanda que acabamos de descrever eh a aprendizagem por correçao de erro discutida na Seçao 2.2. Ela
eh um sistema realimentado de laço fechado, mas o ambiente desconhecido nao esta no laço. Como uma medida de desempenho para o
sistema, podemos pensar em termos do erro medio quadrado ou da soma de erros quadrados sobre a amostra de treinamento, definida
como uma funçao dos parametros livres do sitema. Esta funçao pode ser visualizada como uma superficie multidimencional de
desempenho de erro, ou simplesmente uma superficie de erro, com os parametros livres como coordenadas. A verdadeira superficie
de erro eh oobtida pela media sobre todos os exemplos possiveis de entrada-saida. Qualquer operaçao do sistema sob supervisao
do professor eh representada como um ponto sobre a superficie de erro. Para que o sistema melhore seu desempenho ao longo do
tempo e portanto aprenda com o professor, o ponto de operaçao deve ser movido para baixo sucessivamente em direçao a um ponto
minimo da superficie de erro; o ponto minimo pode ser um minimo local ou um minimo global. Um sistema de aprendizagem
supervisionada eh capaz de fazer isto com a informaçao util que ele tem sobre o gradiente da superficie de erro, correspondente
ao comportamento corrente do sistema. O gradiente de uma superficie de erro em qualquer ponto eh um vetor que aponta na direçao
da descida mais ingrime. Na verdade, no caso da aprendizagem supervisionada por exemplos, o sistema pode usar a estimativa
instantanea do vetor gradiente, supondo que os indices dos exemplos o sistema pode usar a estimativa instantanea do vetor
gradiente, supondo que os indices dos exemplos sejam os mesmos dos instantes de tempo. O uso de tal estimativa resulta em um
movimento do ponto de operaçaosobre a superficie de erro que se da tpicamente na forma de uma "caminhada aleatoria". Apesar
sido, dados um algoritimo projetado para minimizar a funçao de custo, um conjunto adequado de exemplos de entrada-saida e
tempo suficiente para realizar o treinamento, um sistema de aprendizagem supervisionada eh normalmente capaz de realizar
tarefas como classificaçao de padroes e aproximaçao de funçoes.



2.9                                          APRENDIZAGEM SEM UM PROFESSOR

Na aprendizagem supervizionada, o processo de aprendizagem acontece sob a tutela de um professor. Entretantom no paradigma
conhecido como aprendizagem sem um professor, como o nom eusgere, nao ha um professor para supervisionar o processo de
aprendizagem. Isto significa que nao ha exemplos rotulados da funçao a ser aprendida pela rede. Neste segundo paradigma, sao
identificadas duas subdivisoes:


1. Aprendizagem por reforço/Programaçao neurodinamica

Na aprendizagem por reforço, o aprendizado de um mapeamento de entrada-saida eh realizado atraves da interaçao continua com o
ambiente, visando a minimizar um indice escalar de desempenho. A Figura 2.7 representa o diagrama de blocos de forma de sistema
de aprendizagem por reforço construido em torno de um critico que converte um sinal de reforço primario recebido do ambiente em
um sinal de reforço de melhor qualidade, denominado sinal de reforço heuristico, sendo ambos entradas escalares. O sistema eh
projetado para aprender por reforço atrasado, o que significa que o sisteam observa uma sequencia temporal de estimulos (i.e.,
vetores de estado) tambem recebidos do ambiente, que eventualmente resultam na geraçao do sinal de reforço heuristico. O
objetivo da aprendizagem eh minimizar uma funçao de custo para avançar, definida como a expectativa do custo cumulativo de
açoes tomadas ao longo de uma sequencia de passos, em vez de simplismente custo imediato. Pode acontecer que certas açoes
tomadas anteriormente naquela sequencia de passos de tempo sejam de fato os melhores determinantes do comportamento global do
sistema. A funçao da maquina de aprendizagem, que constitui o segundo componente do sistema, eh descobrir estas açoes e
realimenta-las para o ambiente.
    A aprendizagem por reforço atrasado eh dificil de ser realizada por duas razoes basicas:

    *. Nao existe um professor para fornecer uma resposta desejada em cada passo do processo de aprendizagem.
    *. O atraso incorrido na geraçao do sinal de reforço primario implica que a maquina de aprendizagem deve resolver um
       problema de atribuiçao de credito temporal. Com isso, queremos dizer que a maquina de aprendizagem deve ser capaz de
       atribuir credito ou culpa individualmente a cada açao na sequencia de passos de tempo que levam ao resultado final,
       enquanto que o reforço primario eh capaz apenas de avaliar o resultado.

Apesar destas dificuldades, a aprendizagem por reforço atrasado eh muito atraente. Ela fornece base para o sistema interagir
com o seu ambiente, desenvolvendo com isso a habilidade de aprender a realizar uma tarefa predeterminada com base apenas nos
resultados de sua experiencia, que reltam da interaçao.
    A aprendizagem por reforço esta intimamente relacionada com a programaçao dinamica, que foi desenvolvida por Bellman no
contexto da teoria de controle otimo. A programaçao dinamica fornece o formalismo matematico para a tomada de decisao
sequencial. Enquadrando a aprendizagem por reforço dentro da abordagem da programaçao dinamica, o assunto se torna bastante
rico, como demonstrado por Bertsekas e Tsitsiklis (1966). Um tratamento introdutorio sobre programaçao dinamica e sua relaçao
com a aprendizagem por reforço eh apresentado no capitulo 12.

2. Aprendizagem nao-supervisionada

Na aprendizagem nao-supervizionada ou auto-orgranizada, nao ha um professor externo ou um critico para supervisionar o processo
de aprendizado, como indicado na Fig. 2.8. Em vez disso, sao dadas condiçoes para realizar uma medida independente da tarefa da
qualidade da representaçao que a rede deve aprender, e os parametros livre da rede sao otimizados em relaçao a esta medida. Uma
vez que a rede tenha se ajustado `as regularidades estatisticas dos dados de entrada, ela desenvolve a habilidade de formar
representaçoes internas para codificar as caracteristicas da entrada e, desse modo, de criar automaticamente novas classes.


                            Vetor descrevendo o estado do ambiente
            |        |                                                       |                         |
            |AMBIENTE| -------->---------->----------->----------->--------->| SISTEMA DE APRENDIZAGEM |  (Fig. 2.8)
            |        |                                                       |                         |

    Para realizarmos a aprendizagem nao-supervisionada, podemos utilizar a regra de aprendizagem competitiva. Podemos utilizar,
por exemplo, uma rede neural de duas camadas - uma camada de entrada e uma camada competitiva. A camada de entrada recebe os
dados disponiveis. A camada competitiva consiste de neuronios que competem entre si (de acordo com uma regra de aprendizagem)
pela "oportunidade" de responder `as caracteristicas contidas nos dados de entrada. Na sua forma mais simples, a rede opera de
acordo com uma estrategia do tipo, "o vencedor leva tudo". Como descrito na Seçao 2.5, nesta estrategia o neuronio com a maior
entrada total "ganha" a competiçao e se torna ligado; todos os outros neuronios, entao, se tornam desligados.
    Nos capitulos de 8 a 11, sao descritos diferentes algoritimos para aprendizagem nao-supervisionada.



2.10                                            TAREFAS DE APRENDIZAGEM

Nas seçoes anteriores deste capitulo, discutimos diferentes algoritmos de aprendizagem e paradigmas de aprendizagem. Nesta
seçao, descrevemos apenas algumas tarefas basicas de aprendizagem que uma rede neural deve executar. Nest econtexto,
identificamos seis tarefas de aprendizagem que se aplicam ao uso de redes neurais de uma forma ou de outra.


1."Associaçoes de Padroes"

Uma memoria associativa eh uma memoria distribuida inspirada no cerebro, que aprende por associaçao. Desde Aristoteles, sabe-se
que a associaçao eeh uma caracteristica proeminente da memoria humana, e todos os modelos de cogniçao utilizam de uma forma ou
de outra como a operaçao basica.
    A associaçao assume uma de duas formas: auto-associaçao ou heteroassociaçao. Na auto-associaçao, uma rede neural deve
armazenar um conjunto de padroes (vetores), que sao apresentados repetidamente `a rede. Subsequentemente, apresenta-se `a rede
uma descriçao parcial ou distorcida (ruidosa) de um padrao original armazenado e a tarefa eh recuperar (recordar) aquele padrao
particular. A heteroassociaçao difere da auto-associaçao pelo fato de um conjutno arbitrario de padroes de entrada ser
associado a um outro conjunto arbitrario de padroes de saida. A auto-associavolve o uso de aprendizagem nao-supervizionada,
enquanto que, na heteroassociaçao, a aprendizagem eh supervisionada.
    Considere que Xk represente um padrao-chave (vetor) aplicado a uma memoria associativa e Yk represente um padrao memorizado
(vetor). A associaçao de padroes realizada pela rede eh descrita por

                Xk --> Yk,          k = 1,2,....,q.                                 (2.18)

onde q eh o numero de padroes armazenados na rede. O padrao-chave Xk age como um estimulo que nao apenas determina a
localizaçao de armazenamento do padra memorizado Yk, mas tambem eh a chave para sua recuperaçao.
    Em uma memoria auto-associativa, Yk = Xk, e assim os espaços (de dados) de entrada e de saida da rede tem a mesma
dimensionalidade. Em uma memoria heteroassociativa, Yk != Xk; portanto, a dimensionalidade do espaço de saida neste segundo
caso pode ou nao ser igual `a dimensionalidade do espaço de entrada.

    Ha duas fases envolvidadas na operaçao de uma memoria associativa:

    1.A_fase_de_armazenamento, que se refere ao treinamento da rede de acordo com a Eq.(2.18).
    2.A_fase_de_recordaçao, que envolve a recuperaçao de um padrao de memorizado em resposta `a apresentaçao `a rede de uma
versao ruidosa ou distorcida de um padrao-chave.

Suponha que os estimulo (entrada) X represente uma versao ruidosa ou distorcida de um padrao de cahve Xj. Este estimulo produz
uma resposta (saida) y, como indicado na Fig. 2.9. Para a recordaçao perfeita, nos deveriamos obter Y = Yj, onde Yj eh o padrao
memorizado associado ao padrao-chave Xj. Quando Y != Yj, para X = Xj, diz-se que a memoria associativa fez um erro de
recordaçao.

    Vetor de entrada X ----------> Associador de padroes --------> Vetor de saida Y    (2.9)

    O numero q de padroes armazenados em uma memoria associativa fornece uma medida direta da capacidade de armazenamento da
rede. No projeto de uma memoria associativa, o desafio eh tornar a capacidade de armazenamento q (expressa como uma porcentagem
do numero total N de neuronios utilizados para contruir a rede ) tao grande quanto possivel e ainda assim conseguir que uma
grande fraçao dos padroes memorizados sejam recordados corretamente.


2."Reconhecimento de Padroes"

Os seres humandos sao bons no reconhecimento de padroes. Recebemos dados do mundo `a nossa volta atraves dos nossos sentidos e
somos capazes de reconhecer a fonte de dados. Frequentemente somos capazes de fazer isso quase que imediatamente e praticamente
sem esforço. Podemos, por exemplo, reconhecer um rosto familiar de uma pessoa muito embora esta pessoa tenha envelhecido desde
nosso ultimo encontro, identificar uma pessoa familiar pela sua voz ao telefone, apesar de uma conexao ruim, e distinguir um
ovo fervido que eh bom pelo ruim pelo seu cheiro. Os humanos realizam o reconhecimento de padroes atraves de um processo de
aprendizagem; e assim acontece com as redes neurais.
    O reconhecimento de padroes eh formalmente definido como o processo pelo qual um padrao/ sinal recebido eh atribuido a uma
classe dentre um numero predeterminado de classes (categorias). Uma rede neural realiza o reconhecimento de padroes passando
inicialmente por uma seçao de treinamento, durante a qual se apresenta repetidamente `a rede um conjunto de padroes de entrada
junto com a categoria `a qual se apresenta diretamente cada padrao pertence. Mais tarde, apresenta-se `a rede um novo padrao
que nunca foi visto antes, mas que pertence `a mesma populaçao de padroes utilizada para treinar a rede. A rede eh capaz de
identificar a classe daquele padrao particular por causa da informaçao que ela extraiu dos dados de treinamento.O
reconhecimento de padroes realizado por uma rede neural eh de natureza estatistica, com os padores sendo representados por
pontos em um espaço de decisao multidimensional. O espaço de decisao eh dividido em regioes, cada uma das quais associada a uma
classe. As fronteiras de decisao sao determinadas pelo processo de treinamento. A construçao dessas fronteiras eh tornada
estatistica pela variabilidade inerente que existe dentro das classes e entre as classes.
    Em termos genericos, as maquinas de reconhecimento de padroes que utilizam redes neurais podem assumir uma das duas formas
seguintes:

    *. A maquina eh dividida em duas partes, uma rede nao-supervisionada para extraçao de caracteristicas e uma rede
supervisionada para classificaçao, como mostrado na figura 2.10a. Este metodo segue a abordagem tradicional de reconhecimento
estatistico de padroes. Em termos conceituais, um padrao eh representado por um conjunto de m observaveis, que pode ser visto
como um ponto X de um espaço de observaçao (de dados) m-dimensional. A extraçao de caracteristicas eh descrita por uma
transformaçao que mapeia o ponto X para um ponto intermediario Y em um espaço de caracteristicas q-dimensional, com q < m, como
indicado na figura 2.10b. Esta transformaçao pode ser vista como uma reduçao de dimensionalidade (i.e., compressao de dados),
cuja utilizaçao eh justificada por ela simplificar a tarefa de classificaçao. A propria classificaçao eh descrita como uma
transformaçao que mapeia o ponto intermediario Y para uma das classes em um espaço de dimensao r-dimensional, onde r eh o
numero de classes a ser distinguidas.
    *. A maquina eh projetada como uma unica rede de multiplas camadas alimentadas adiante, utilizando um algoritmo de
aprendizagem supervisionada. Nesta segunda abordagem, a tarefa de extraçao de caracteristicas eh realizada pelas unidades
computacionais da(s) camada(s) oculta(s) da rede.

A escolha de qual destas duas abordagens deve ser adotada na pratica depende da aplicaçao de interesse.

3."Aproximaçao de Funçoes"

A terceira tarefa de aprendizagem de interesse eh a aproximaçao de funçoes. Considere um mapeamento de entrada-saida nao-linear
descrito pela relaçao funcional

                                    D = f(X)    (Eq. 2.19)

onde o vetor X eh a entrada e o vetor D eh a saida. Supoe-se que a funçao de valor vetorial f(.) seja desconhecida. Para
compensar a falta de conhecimento sobre a funçao F(.), eh fornecido um conjunto de exemplos rotulados:

                                    R = {(Xi,Di)}[i=1,N]    (Eq. 2.20)

O objetivo eh projetar uma rede neural que aproxime a funçao desconhecida f(.) de forma que a funçao F(.) que descreve o
mapeamento de entrada-saida realmente realizado pela rede esteja suficientemente proxima de f(.), em um sentido euclidiano,
sobre todas as entradas, como mostrado por

                                    ||F(X) - f(X)|| < e   para todo X   (Eq. 2.21)

onde 'e' eh um numero positivo pequeno. Contanto que o tamanho N do conjunto de treinamento seja suficientemente grande e que a
rede esteja equipada com um numero adequado de parametros livres, entao pode-se fazer o erro aproximatico 'e' suficientemente
pequeno para a tarefa.
    O probelma de aproximaçao descrito aqui eh um candidato perfeito para a aprendizagem supervisionada, com Xi desempenhando o
papel de vetor de entrada e Di desempenhando o papel da resposta desejada. Podemos entao inverter esta questao e ver a
aprendizagem supervisionada como um problema de aproximaçao.
    A habilidade de uma rede neural de aproximar um mapeamento de entrada-saida desconhecido pode ser explorada de duas formas
importantes:

    1.Identificaçao_de_sistemas. Suponha que a equaçao (2.19) descreva a relaçao de entrada-saida de um sistema de multiplas
    entradas- multiplas saidas (MIMO, multiple input-multiple output) sem memoria, desconhecido; entedemos por sistema
    "sem memoria" um sistema que seja invariante no tempo. Podemos entao utilizar o conjunto de exemplos rotulados da equaçao
    (2.20) para treinar uma rede neural como um modelo do sistema. Suponha que Yi represente a saida da rede neural produzida
    por um vetor de entrada Xi. A diferença Di (associado com Xi) e a saida da rede Yi fornece o vetor de sinal de erro Ei,
    como representado na figura 2.11. Este sinal de erro, por sua vez, eh usado oara ajustar os parametros livres da rede de
    forma a minimizar a diferença quadratica entre as saidas do sistema e a rede neural em um sentido estatistico, e eh
    calculado sobre o conjunto de treinamento inteiro.
    2.Sistema_inverso. Suponha a seguir que nos seja fornecido um sistema MIMO conhecido, sem memoria,cuja relaçao de
    entrada-saida eh descrita pela equaçao (2.19). O objetivo neste caso ej construir um sistema inverso que produza o vetor X
    em resposta ao vetor D. O sistema inverso pode, assim, ser descrito por

                                        X = f(D)^(-1)   (Eq. 2.22)

    onde a funçao de valor vetorial f(.)^(-1) representa a inversa de f(.). Em muitas situaçoes encontradas na pratica, a
    funçao de valor vetorial f(.) eh por demais complexa para que se possa formular diretamente a sua funçao inversa. Dado o
    conjunto de exemplos rotulados da equaçao (2.20), podemos construir uma aproximaçao por rede neural de f(.)^(-1), utilizando
    o esquema mostrado na Fig. 2.12. Na situaçao aqui descrita, os papeis de Xi e Di foram trocados: o vetor Di eh utilizado
    como a entrada e Xi eh tratado como a resposta desejada. Suponha que o vetor de sinal de erro Ei represente a diferença
    entre Xi e a saida real Yi da rede neural, produzida em resposta a Di. Como no problema de identificaçao de sistemas, este
    vetor de sinal de erro eh utilizado para ajustar os parametros livres da rede neural, de modo a minimizar a diferença
    quadratica entre as saidas do sistema invers desconhecido e da rede neural em um sentido estatistico, e eh calculado sobre
    o conjunto de treinamento completo.


4."Controle"

O controle de uma planta eh outra tarefa de aprendizagem que pode ser feita por uma rede neural; aqui, "planta" significa um
processo ou uma parte critica de um sistema que deve ser mantido em uma condiçao controlada. A relevancia da aprendizagem para
o controle nao deveria ser surpreendente porque, afinal, o cerebro humano eh um computador (i.e., um processador de
informaçao), que, visto como um sistema, produz saidas que sao açoes. No contexto de controle, o cerebro eh a prova viva de que
eh possivel construir um controlador generico que tira total vantagem da implementaçao fisica paralelamente distribuida, que
pode controlar muitos milhares de atuadores (fibras musculares) em parelelo, que pode tratar nao-linearidades e ruido e que
pode realizar otimizaçao sobre um horizonte de planejamento muito amplo.
    Considere o sistema de controle realimentado da Fig. 2.13. O sistema envolve o uso de realimentaçao unitaria em torno de
uma planta a ser controlada; isto eh, a saida da planta eh realimentada diretamente para a entrada. Com isso, asaida da planta
'Y' eh subtraida de um sinal de referencia D fornecido por uma fonte externa. O sinal de erro 'e' assim produzido eh aplicado a
um controlador neural com o proposito de ajustar os seu parametros livres. O objetivo principal do controlador eh fornecer
entradas apropriadas para a planta, fazendo com que a sua saida Y siga o sinal de referencia 'D'. Em outras palavras, o
controlador deve inverter o comportamento de entrada-saida da planta.
    Notamos que na Fig. 2.13 o sinal de erro 'e' deve-se propagar atravez do controle neural antes de alcançar a planta.
Consequentemente, para realizar sjustes nos parametros livres da planta de acordo com um algoritmo de aprendizagem por correçao
de erros, precisamos conhecer a matriz jacobiana

                                        J = {DP("Yk")/DP("Uj")}     (Eq. 2.23)

onde "Yk" eh um numero da saida da planta "Y" e e "Uj" eh mu elemento de entrada da planta U. Infelizment, as derivadas
parciais "Yk/Uk" para varios "k" e "j" dependem do ponto de operaçao da planta e, portanto, nao sao conhecidas. Podemos adotar
uma de duas abordagens para tratar este problema:

    1.Aprendizagem_indireta. Utilizando medidas de entrada-saida reais da planta, eh construido inicialmente um modelo baseado
    em rede neural para produzir uma copia de planta. Por sua vez, este modelo eh utilizado para fornecer uma estimativa da
    matriz jacobiana J. As derivadas parciais que constituem esta matriz jacobiana sao utilizadas subsequentemente no algoritmo
    de aprendizagem por correçao de erro para calcular os ajustes dos parametros livres do controlador neural.
    2.Aprendizagem_direta. O sinais das derivadas parciais DP(Yk)/DP(Uj) sao geralmente conhecidos e normalmente se mantem
    constantes ao longo do nitervalo sinamico da planta. Isto sugere que podemos aproximar estas derivadas parciais pelos seus
    sinais individuais. Os seus valores absolutos recebem uma representaçao distribuida nos parametros livres d controlador
    neural.Com isso, o controlador neural se torna capacitado a aprender os ajustes de seus parametros livres diretamente
    da planta.


5."Filtragem"

O termo "filtro" se refere frequentemente a um dispositivo ou algoritmo utilizado para extrais informaçao sobre uma determinada
grandeza de interessa a partir de um conjunto de dados ruidosos. O ruido pode surgir de uma variedade de fontes. Os dados podem
ter sido medidos por meio de sensores ruidosos, por exemplo, ou podem representar um sinal de portador de informaçao que foi
corrompido pela transmissao atraves de um canal de comunicaçao. Como outro exemplo, pode-se ter uma componete de sinal util,
corrompida por sinal de interferencia captado do meio ambiente. Podemos utilizar um filtro para realizar tres tarefas basicas
de processamento de informaçao:

  1.Filtragem. Esta tarefa se refere `a extraçao de informaçao sobre uma quantidade de interesse no tempo discreto 'n',
    utilizando dados medidos ate o tempo 'n', inclusive.
  2.Suavizaçao. Esta segunda tarefa difere da filtragem pelo fato de que nao eh necessario que a informaçao sobre a grandeza de
    interesse esteja disponivel no tempo 'n' e de que os dados medidos apos o tempo 'n' podem ser usados para obter esta
    informaçao. Isto significa que, na suavizaçao, ha um "atraso" na produçao do resultado de interesse. Ja que no processo de
    suavizaçao podemos usar dados obtidos nao apenas ate o tempo 'n' mas tambem apos o tempo 'n', podemos esperar que a
    suavizaçao seja mais precisa que a filtragem em sentido estatistico.
  3.Previsao. Esta tarefa corresponde ao lado preditivo do processamento de informaçao. O objetivo aqui eh derivar informaçao
    sobre como sera a grandeza de interesse em um determinado tempo 'n' + 'n0' no futuro, para algum 'n0' > 0, utilizando os
    dados medidos ate o tempo 'n' inclusive.

Um problema de filtragem com qual os seres humanos estao familiarizados eh o problema da festa de coquetel. Temos uma
habilidade notavel para nos concentrarmos em um locutor dentro de um ambiente ruidoso de uma festa de coquetel, apesar de o
sinal de voz originario daquele locutor esta envolvido por um fundo extremamente ruidoso devido `a interferencia de outras
conversas na sala. Presume-se que alguma forma de analise pre-atentiva, pre-consciente deve estar envolvida na resoluçao do
problema da festa de coquetel. No contexto das redes neurais (artificiais), um problema similar de filtragem ocorre na chamada
"separaçao cega de sinal". Para formular o problema da separaçao cega de sinal, considere um conjunto de sinais de fonte
desconhecidos {Si(n)}[i=1, m], que sao mutuamente independentes entre si. Estes sinais sao misturados linearmente por um um
sensor desconhecido para produzir um vetor de observaçao m-por-1.

                                        X(n) = A U(n)   (Eq. 2.24)

onde

                                        U(n) = [U1(n),U2(n),...,Um(n)]^T    (Eq. 2.25)

                                        X(n) = [X1(n),X2(n),...,Xm(n)]^T    (Eq. 2.26)

e 'A' eh uma "matriz de mistura" nao-singular, desconhecida, de dimensaoes m-por-m. Dado o vetor de observaçao X(n), o objetivo
eh recuperar os sinais originais U1(n),U2(n),...,Um(n) de uma maneira nao-supervisionada.
    Voltando-se agora ao problema da previsao, o objetivo eh prever o valor presente X(n) de um processo, dados valores
passados deste processo, que sao uniformemente espaçados no tempo, como mostrado por X(n-1T),X(n-2T),...,(n-mT), onde T eh o
periodo de amostragem e 'm' eh a ordem da previsao. A previsao pode ser resolvida utilizando-se aprendizagem por correçao de
erro de uma maneira nao-supervisionada, ja que os exemplos de treinamento sao retirados diretamente do proprio processo, como
representado na Fig. 2.15, onde X(n) atua como resposta desejada. Suponha que X^(n) represente a previsao de um passo produzida
pela rede neural no tempo 'n'. O sinal de erro E(n) eh definido como a diferença entre X(n) e X^(n), que eh usada para ajustar
os parametros livres da rede neural. Com isso, a previsao pode ser vista como uma forma de "construçao de modelo", significando
que qunato menor for o erro de previsao em um sentido estatistico, melhor sera o desempenho da rede como um modelo do processo
fisico basico que eh responsavel pela geraçao dos dados. Quando este processo eh "nao-linear", o uso de uma rede neural fornece
um metodo poderoso para resolver o problema de previsao, devido as unidades de processamento nao-lineares que podem ser usadas
nesta construçao. Entretanto, a unica exceçao possivel para o uso de unidades de processamento nao-lineares eh a unidade de
sauda da rede: se o intervalo dinamico da serie temporal {X(n)} for desconhecido, a utilizaçao de uma unidade de saida linear
eh a ecolha mais razoavel.


6."Formaçao de feixe"

A formaçao de feixe eh uma forma de filtragem espacial e eh utilizada para distinguir entre as propriedades espaciais de um
sinal-alvo e o o ruido de fundo. O dispositivo usado para realizar a formaçao de feixe eh chamado de formador de feixe.
    A tarefa de formaçao de feixe eh compativel com o uso de uma rede neural, para o que temos indicaçoes importantes de
estudos da psico-acustica das respostas auditivas humanas e de estudos do mapeamento de caracteristicas nas camadas corticais
dos sistemas auditivos de morcegos eco-localizadores. O morcego ecolocalizador irradia o meio ambiente transmitindo sinais de
frequencia modulada (FM) de curta duraçao e entao utiliza o seu sistema auditivo para focar a atençao na sua presa. As orelhas
fornecem ao morcego uma forma de filtragem espacial (interferometria, para sermos exatos), que eh entao explorada pelo sistema
auditivo para produzir uma seletividade por atençao.
    A formaçao de fiexe eh normalente utilizada em sistemas de radar e sonar nos quais a tarefa principal eh detectar e
perseguir um alvo de interesse na presença combinada de ruido do receptor e inal de interferencia (p.ex., obstrutores). Esta
tarefa eh complicada por dois fatores.

    *. O sinal-alvo se origina em uma direçao desconhecida.
    *. Nao h ainformaçao a priori disponivel sobre os sinais de interferencia.

Uma forma de lidar com situaçoes deste tipo eh utilizando um cancelador de lobulo lateral generalizado (CLLG), cujo diagrama em
blocos esta mostrado na Fig. 2.16. O sistema consiste dos seguintes componentes :

    *. Um arranjo de elementos de antenas, que fornece um meio de amostrar o sinal observado em pontos discretos de espaço.
    *. Um combinador linear definido por um conjunto de pesos fixos {Wi}[i=1,m], cuja saida eh uma resposta desejada. Este
       combinador linear age como um "filtro espacial", sendo caracterizado por um padrao de radiaçao (i.e., um grafico polar
       da amplitude de saida da antena em funçao do angulo de incidencia de um sinal incidente). O lobulo principal deste
       padrao de radiaçao esta apontado ao longo de uma direçao predeterminada, para a qual o CLLG deve ser restrito para
       produzir uma resposta desejada para o formador de feixe.
    *. Uma matriz bloqueadora de sinal Ca, cuja funçao eh cancelar a interferencia que escapa atraves dos lobulos laterais do
       padrao de radiaçao do filtro esppacial que representa o combinador linear.
    *. Uma rede neuarl com parametros ajustaveis, que eh projetada para acomodar variaçoes estatisticas nos sinais de
       interferencia.

Os ajustes dos parametros livres da rede neural sao realizados por um algoritmo de aprendizagem por correçao de erro que opera
sobre o sinal 'E(n)', definido como a diferença entre a saida do combinador linear 'D(n)' e a saida real 'Y(n)' da rede neural.
Assim, o CLLG opera sob a supervisao do combinador linear que assume o papel de um "professor". Como na aprendizagem
supervisionada usual, note que um combinador linear esta fora laço de realimentaçao que age sobre a rede neural. Um formador de
feixe que que utiliza uma rede neuarl para a aprendizagem eh chamado de formador de deixe neural. Esta classe de maquinas de
aprendizagem se enquadra sob o titulo geral de neurocomputadores atencioanis.
    A diversidade das seis tarefas de aprendizagem discutidas aqui serve de testemunha para a universialidade das redes neurais
como sistemas de processamento de informaçao. Em um sentido fundamental, todas as tarefas de aprendizagem sao problemas
relativos a aprender um mapeamento a partir de exemplos (possivelmente ruidosos) de mapeamentos. Sem a imposiçao de
conhecimento previo, cada uma destas tarefas eh na verdade mal-formulada, no sentido de nao-unicidade das possiveis doluçoes de
mapeamento. Um metodo de tornar a soluçao bem-formulada eh utilizar a teoria da regularizaçao, que sera descrita no capitulo 5.



2.11                                                    MEMORIA

A discussao de tarefas de aprendizagem, paricularmente a tarefa de associaçao de pafroes, nos leva naturalmente a refletir
sobre a memoria. Em um contexto neurobiologico, memoria se refere `as alteraçoes neurais relativamente duradouras induzidas
pela interaçao de um orgranismo com o seu ambiente. Sem esta alteraçao nao pode haver memoria. Alem disso, para que a memoria
seja util, ela deve ser acessivel ao sistema nervoso para poder influenciar o comportamento futuro. Entretanto, um padrao de
atividade deve ser inicialmente armazenado na memoria atraves de um processo de aprendizagem. Memoria e aprendizagem estao
conectadas de forma intrincada. Quando um padrao de atividade particular eh aprendido, ele eh armazenado no cerebro, de onde
pode ser recuperado mais tarde, quando exigido. A memoria se divide em memoria de "curto prazo" e de "longo prazo", dependendo
do tempo de retençao. 1.Memoria_de_curto_pazo se refere a uma compilaçao de conhecimento que representa o estado "corrente" do
ambiente. Quaisquer discrepancias entre o conehcimento armazenado na memoria de curto prazo e um "novo" estado sao usados para
atualizar a memoria de curto prazo. 2.Memoria_de_longo_prazo, por outro lado, se refere ao conhecimento armazenado por um longo
periodo ou permanentemente.
    Nesta seçao, estudamos uma memoria associativa que oferece as seguintes caracteristicas:

    *.  A memoria eh distribuida.
    *.  Tanto os padroes de estimulo (chave) como os padroes de resposta (armazenados) de uma memoria associativa consistem de
        vetores de dados.
    *.  A informaçao eh armazenada na memoria estabelecendo-se um padrao espacial de atividades neurais atraves de um grande
        numero de neuronios.
    *.  A informaçao contida em um estimulo nao apenas determina o seu local de armazenamento mas tambem o endereço para a sua
        recuperaçao.
    *.  Embora os neuronios nao representem celulas computacionais confiaveis e de baixo ruido, a memoria exibe um alto grau de
        resistencia a ruido e a falhas, de uma forma difusa.
    *.  Pode haver interaçoes entre padroes individuais armazenados na memoria. (De outra forma, a memoria deveria ser
        excepcionalmente grande para acomodar o armazenamento de um grande numero de padroes em perfeito isolamento entre si.)
        Existe, portanto, a possibilidade de a meomoria cometer erros durante o processo de recordaçao.

Em uma memoria distribuida, a questao basica de interesse sao as ativades simultaneas ou quase simultaneas de muitos neuronios
diferentes, que sao o resultado de estimulos externos ou internos. As atividades neurais formam um padrao espacial dentro da
memoria que contem informaçao sobre os estimulos. Diz-se, portanto, que a memoria realiza um mapeamento distribuid que
transforma um padrao de atividade no espaço de entrada em um outro padrao de atividade no espaço de saida. Podemos ilustrar
algumas propriedades importantes de um mapeamento de memoria distribuida onsiderando uma rede neural idealizada que consiste de
duas camadas de neuronios. A figura 2.17a ilustra uma rede que pode ser vista como um componente modelo de um sistema nervoso.
Cada neuronio da camada de entrada esta conectada a todos os neuronios da camada de saida. As conexoes sinapticas reais entre
os neuronios sao complexas e redundantes. No modelo da Fig. 2.17a, uma unica junçao idela eh utilizada para representar o
efeito integrado de todos os contatos sinapticos entre os dendritos de um neuronio da camada de entrada e os ramos do axionio
de um neuronio da camada de saida. O nivel de atividade de um neuronio da camada de entrada pode afetar o nivel de atividade de
todos os outros neuronios da camada de saida.
    A situaçao correspondente para uma rede neural artificial esta representada na Fig. 2.17b. Aqui temos uma camada de entrada
de nos de fonte e uma camada de saida de nueronios agindo como nos computacionais. Neste caso, os pesos sinapticos da rede
estao incluidos como partes integrantes dos neuronios da camada de saida. Os elos de conexao entre as duas camadas da rede sao
simplesmente fios.
    Na analise matematica seguinte, supoe-se que ambas as redes neurais das figuras sao lineares. A implicaçao desta suposiçao
eh que cada neuronio age como um combinador linear, como representado no grafo de fluxo de sinal da figura 2.18. Para
prosseguir com a analise, suponha que um padrao de atividades 'Xk' ocorra na camada de entrada da rede e que um padrao de
atividade 'Yk' ocorra simultaneamente na camada de saida. A questao que desejamos considerar aqui eh a aprendizagem da
associaçao entre os padroes 'Xk' e 'Yk'. Onde :

                            'Xk' = ['Xk1','Xk2',...,'Xkm']^T

                            'Yk' = ['Yk1','Yk2',...,'Ykm']^T

Por conveniencia de apresentaçao, supomos que a dimensionalidade do espaço de entrada (i.e., a dimensao do vetor 'Xk') eh a
mesma que a dimensionalidade do espaço de saida (i.e., a dimensao do vetor 'Yk') e igual a 'm'. De agora em diante, nos nos
referimos a 'm' como a dimensionalidade da rede ou simplismente a dimensionalidade. Note que 'm' eh igual ao numero de nos de
fonte na camada de entrada de neuronios na camada de saida. Para uma rede neural com um grande numero de neuronios, que eh o
caso tipico, adimensionalidade 'm' pode ser grande.
    Os elementos tanto de 'Xk' como de 'Yk' podem assumir valores positivos e negativos. Esta eh uma proposiçao valida em uma
rede neural artificial. Isto tambem pode ocorrer em um sistema nervoso, considerando que a variavel fisiologica relevante seja
a diferença entre um nivel de atividade real (p.ex., a taxa de disparo de um neuronio) e um nivel de atividade espontaneo
diferente de zero.
    Supondo que as redes da Fig. 2.17 sejam lineares, a associaçao do vetor-chave 'Xk' com o vetor memorizado 'Yk' pode ser
descrita na forma matricial como:

                            'Yk' = 'W(k)'*'Xk' ,    k=1,2,...,q     (Eq. 2.27)

onde 'W(k)' eh uma matriz de pesos determinada apenas pelo par de entrada-saida ('Xk', 'Yk').
    Para desenvolvermos uma descriçao detalhada da matriz de pesos 'W(k)', considere a Fig. 2.18, que mostra um arranjo
detalhado do neuronio 'i' na camada de saida. A saida 'Yki' do neuronio 'i' devido `a açao combinada dos elementos do
padrao-chave 'Xk' aplicado como estimulo `a camada de entrada eh dada por

                            'Yki' = SUM('Wij(k)'*'Xkj')[j=1,m], i = 1,2,...,m   (Eq. 2.28)

Monta-se entao uma matriz de pesos m-por-m 'W(k)' como os elementos Wkj.
As apresnetaçoes individuais dos q pares de padroes associados 'Xk' --> 'Yk', k = 1,2,...,q, produzem valores correspondentes
da matriz individual, ou seja, 'W(1)','W(2)',...,'W(q)'. Reconhecendo que esta representaçao depadroes eh representada pela
matriz de pesos 'W(k)', podemos definir uma matriz de memoria m-por-m que descreve a soma das matrizes de pesos para o conjunto
inteiro de associaçoes de padroes como segue:

                            'M' = SUM('W(k)')[k=1,q]    (Eq. 2.32)

A matriz de memoria 'M' define a conectividade global entre as camadas de entrada e de saida da memoria associativa. Na
verdade, ela representa a experiencia total ganha pela memoria como resultado das representaçoes de 'q' padroes de
entrada-saida. Dito de outra forma, a matriz de memoria 'M' contem uma parte de cada par de entrada-saida dos padroes de
atividade apresentados `a memoria.
    A definiçao da matriz de memoria dada pela Eq. (2.32) pode ser reestruturada em forma recusiva como mostrado por

                            'Mk' = 'M(k-1)' + 'W(k)',   k = 1,2,...,q       (Eq. 2.33)

onde o valor inicial 'M0' eh zero (i.e., os pesos sinapticos da memoria sao inicialmente todos zeros), e o valor final 'Mq' eh
identicamente igual a 'M' como definido na equaçao (2.32). De acordo com a formula recursiva da Eq.(2.33), o termo 'M(k-1)' eh
o valor antigo da matriz de memoria resultante das associaçoes de padroes (k-1), e 'Mk' eh o valor atualizado devido ao
incremento 'W(k)' produzido pela k-esima associaçao. Note, entretanto, que quando 'W(k)' eh adicionado a 'M(k-1)', o incremento
'W(k)' perde a sua identidade entre a mistura de contribuiçoes que formam 'Mk'. apesar da mistura sinaptica de diferentes
associaçoes, a informaçao sobre os estimulos pode nao ter sido perdida, como sera demonstrado a seguir. Note tambem que quano o
numero 'q' de padroes armazenados aumenta, a influencia de um novo padrao na memoria como um todo eh progressivamente reduzida.



"Memoria por Matriz de Correlaçao"

Suponha que a memoria associativa da Fig. 2.17b aprendeu a matriz de memoria 'M', atraves das associaçoes de padroes-chaves e
padroes memorizados descritos por 'Xk' --> 'Yk', onde k = 1,2,...,q. Podemos postular 'M^', que representa uma estimativa da
matriz de memoria 'M' em termos destes padroes, como:

                            'M^' = SUM( 'Yk'*('Xk'^T) )[k=1,q]      (Eq. 2.34)

O termo  'Yk'*('Xk'^T) representa o produto externo entre o padrao-chave 'Xk' e o padrao memorizado 'Yk'. Este produto externo
eh uma "estimativa" da matriz de pesos 'W(k)' que mapeia o padrao de saida 'Yk' para o padrao de entrada 'Xk'. Como, por
suposiçao, ambos os padroes 'Xk' e 'Yk' sao ambos vetores m-por-1, segue que o produto externo eh uma matriz m-por-m.

                            'M^' = ['y1','y2',...,'yq']['x1^T','x2^T',...,'xq^T']^T         (Eq. 2.35)
                             = 'Y'*('X'^T)

onde a matriz X eh chamada de matriz-chave. A matriz Y eh uma matriz chamada de matriz-memorizada.


"Recordaçao"

O problema fundamental originado pelo uso de uma memoria associativa eh o endereçamento e a recordaçao de padroes armazenados
na memoria. Para explicar um aspecto deste problema, suponha que 'M^' represente a matriz de memoria correspondente a uma
memoria associativa, que tenha sofrido um processo completo de aprendizagem, pela sua exposiçao a 'q' associaçoes de padroes,
de acordo com a Eq. (2.34). Suponha que um padrao-chave 'xj' seja escolhido ao acado e reaplicado como um estimulo para a
memoria, produzindo a resposta.

                            'y' = 'M^'*'xj'         (Eq. 2.39)

substituindo a  Eq.(2.34) em (2.39), obtemos

                                                    (Eq. 2.40)

onde, nasegunda liha, reconhecendo que 'Xk^T''Xj' eh um escalr igual ao produto interno dos vetores chave 'xk' e 'xj'. Podemos
escrever a Eq. (2.40) como

                                                    (Eq. 2.41)

suponha que cada um dos padroes-chave 'x1','x2',...,'xq' sej anormalizado para ter energia unitaria; isto eh,

                                                    (Eq. 2.42)

Consequentemente, podemos simplificar a resposta da memoria ao estimulo (padrap-chave) 'Xj' como

                                                    (Eq. 2.43)

onde

                                                    (Eq. 2.44)

O primeiro termo no lado direito da equaçao (2.43) representa a resposta "desejada" 'yj'; ELE PODE SER VISTO, PORTANTO, COMO A
COMPONETE DO "sinal" da resposta real 'y'. O segundo termo 'vj' eh um "vetor de ruido" que surge devido `a interferencia
cruzada entre o vetor-chave 'xj' e todos os outros vetores-chave armazenados na memoria. O vwtor de ruido 'vj' eh responsavel
pelos erros de recordaçao.
    No contexto de um espaço de sinal linear, podemos definir o cosseno do angulo entre um par de vetores 'Xj' e 'Xk' como o
produto interno de 'Xj' e 'Xk', dividido pelo produto de suas normas euclidianos ou comprimento, como mostrado por

                                                    (Eq. 2.45)

A norma euclidiana do vetor 'Xk' eh definida como a raiz quadrada da energia de 'Xk':

                                                    (Eq. 2.46)

Retornando a situaçao em questao, note que os vetores-chave sao normalizados para terem energia unitaria de aconrdo aom a
queaçao (2.42). Podemos, portanto, reduzir a definiçao da equaçao (2.45) a

                                                    (Eq. 2.47)

Podemos entao definir o vetor de ruido da Eq. (2.44) como

                                                    (Eq. 2.48)

Vemos agora qu ese os vetores-chave forem ortogonais (i.e., perpendiculares entre si no sentido euclidiano), entao

                                                    (Eq. 2.49)

e, portanto, o vetor de ruido 'vj' eh igual a zero. Neste caso, a resposta 'y' iguala a resposta 'yj'. A memoria associa
perfeitamente se os vetores-chave pertencem a um conjunto-ortonormal; isto eh, se eles satisfazerem o seguinte par de condiçoes:

                                                    (Eq. 2.50)

suponha agora que os vetores-chave formam um conjunto ortonormal, como descrito pela equaçao (2.50). Qual eh entao o limite da
capacidade de armazenamento da memoria associativa? Dito de outra forma, qual eh o maior numero de padroes que podem ser
armazenados de forma confiavel? A resposta a esta questao fundamental se encontra no posto da matriz de memoria 'M^'. O posto
de uma matriz eh definido como o numero de colunas (linhas) independentes da matriz. Isto eh, se 'r' eh o posto de uma matriz
retangular de dimesoes l-por-m, temos entao que r<=min(l,m). No caso da memoria por correlaçao, a matriz de memoria 'M^' eh uma
matriz m-por-m, onde m eh a dimensionalidade do espaço de entrada. Assim, o posto da matriz de memoria M eh limitado pela
dimensinalidade m. Podemos entao formalmente afirmar que o numeor de padroes que podem ser armazenados de forma confiavel em
uma memoria por matriz de correlaçao nunca pode exceder a dimensionalidade do espaço de entrada.
    Em situaçoes do mundo real, frequentemente observamos que os padroes-chave apresentados a uma memoria associativa nao sao
nem ortogonais nem estao muito separados entre si. Consequentemente, uma memoria por matriz de corelaçao caracterizada pela
matriz de memoriada Eq. (2.34) pode algumas vezes se confundir e ocasionar erros. Isto eh, a memoria ocasionalmente reconhece e
associa padroes que antes nunca forma vistos ou associados. Para ilustrar esta propriedade de uma memoria associativa,
considere um conjunto de padroes-chave.

                                                    {'Xchave'}:'X1','X2',...,'Xq'

e um conjunto correspondente de padroes memorizados,

                                                    {'Ymem'}:'Y1','Y2',..,'Yq'

Para expressar a proximidade dos padroes-chave em um espaço de sinais lineares, introduzimos o conceito de comunidade.
Definimos a comunidade do conjunto de padroes {'Xchave'} como o limite inferior dos produtos internos 'Xk'^T*'Xj' de dois
padroes quaisquer 'xj'e 'xk' do conjunto. Suponha que 'M^' represente a matriz de memoria resultante do treinamento da memoria
associativa com um conjunto de padroes-chave representado por {'Xchave'} e um conjunto correspondente de padroes memorizados
{'Ymem'}, de acordo com a Eq. (2.34). A resposta da memoria, 'y', a um estimulo 'Xj' selecionado do conjunto {'Xchave'} eh dada
pela equaçao (2.39), onde supomos que cada padrao do conjunto {'Xchave'} eh um vetor unitario (i.e., um vetor com energia
unitaria). Suponhamos ainda que

                                                (Eq. 2.51)

Se o limite inferior y for suficientemente grande, a memoria pode falhar em distinguir a resposta y daquela de qualquer outro
padra-chave contido no conjunto {'Xchave'}. Se os padroes-chave deste conjunto tiverem a forma

                                                (Eq. 2.52)

onde 'v' eh um vetor esstocastico, eh provavel que a memoria reconheça 'X0' e o associe a um vetor 'y0' em vez de associa-lo a
qualquer um dos pares de padroes reais utilizados inicialmente para treina-la; 'x0' e 'y0' representam um par de padroes nunca
vistos anteriormente. Este fenomeno pode ser chamado de logica animal, apesar de nao ser nada logico.



2.12                                            ADAPTAÇAO

Na realizaçao de uma tarefa de interesse, frequentemente constatamos que o espaço eh uma dimensao fundamental do processo de
aprendizagem; o tempo eh a outra. A natureza espaço-temporal da aprendizagem eh exemplificada por muitas das tarefas de
aprendizagem (p.ex., controle, formaçao de feixe) discutidas na Seçao 2.10. TOdas as especies, desde insetos ate os humanos,
tem uma capacidade inerente de representar a estrutura temporal da experiencia. Uma representaçao assim torna possivel para um
animal adaptar seu comportamento `a estrutura temporal de um evento em seu espaço de comportamento.
    Quando uma rede neural opera em um ambiente estacionario (i.e., um ambiente cujas caracteristicas estatisticas nao mudam
com o tempo), as estatisticas essenciasis d ambiente podem ser, em teoria, aprendidas pela rede, sob supervisao de um
professor. Em particular, os pesos sinapticos da rede podem ser calculados submetendo-se a rede a uma sessao de treinamento com
um conjunto de dados que eh representativo do ambiente. Uma vez que o processo de treinamento esteja completo, os pesos
sinapticos da rede capturariam a estrutura estatistica subjacente do ambiente, o que significaria o "conjelamento" de seus
valores depois disso. Assim, o sistema de aprendizagem se baseia de uma frma ou de outra na memoria, para recordar e explorar
experiencias passadas.
    Frequentemente, entretanto, o ambiente de interesse eh nao-estacionario, o que significa que os parametros estatisticos dos
sinais portadores de informaçao, gerados pelo ambiente variam com o tempo. Em situaçoes deste tipo, os metodos tradicionais de
aprendizagem supervisionada podem se mostrar inadequados, pois a rede nao esta equipada com os meios necessarios para seguir as
variaçoes estatisticas do ambiente no qual opera. Para superar esta dificuldade, eh desejavel que uma rede neural possa adaptar
continuamente seus parametros livres `as variaçoes do sinal incidente em tempo real. Assim, um sistema adaptativo responde a
toda a entrada distinta como sendo uma entrada nova. Em outras palavras, o processo de aprendizagem encontrado em um sistema
adaptativo nunca para, com a aprendizagem sendo realizada enquanto o processamento de sinal esta sendo executado pelo sistema.
Esta forma de aprendizagem eh chamada de aprendizagem continua ou aprendizage em tempo real.
    Os filtros adaptativos lineares, construidos em torno de um combinador linear (i.e., um unico neuronio operando em seu modo
linear), sao projetados para realizar aprendizagem continua. Apesar da sua estrutura simples (e talvez por causa disso), eles
sao utilizados largamente em aplicaçoes tao diversas como radar, sonar, comunicaçoes, sismologia e processamento de sinal
biomedico. A teoria dos filtros adaptativos lineares atingiu um estagio de desenvolvimento de elevada maturidade. Entretanto, o
mesmo nao pode ser dito sobre os filtros adaptativos nao-lineares.
    Considerando que a aprendizagem continua seja a propriedade de interesse e uma rede neural o veiculo para a sua
implementaçao, a questao que devemos abordar eh: como uma rede neural pode adaptar seu comportamento `a estrutura temporal
variavel dos sinais incidentes no espaço de comportamentos? Uma forma de abordar esta questao fundamental eh reconhecendo que
as caracteristicas estatisticas de um processo nao-estacionario normalmente variam de forma suficientemente lenta para que o
processo seja considerado pseudo-estacionario em uma janela de tempo com duraçao suficientemente curta. Incluem-se como
exemplos:

    *.  O mecanismo responsavel pela produçao de um sinal de voz pode ser considerado essencialmente estacionario durante um
        periodo de 10 a 30 milissegundos.
    *.  Ondas de radar retornadas de uma superficies do oceano pemanecem essencialmente estacionarias por um periodo de varios
        segundos.
    *.  Considerando-se a previsao do tempo a longo prazo, os dados metereologicos podem ser vistos como essencialmente
        estacionarios durante um periodo de minutos.
    *.  No contexto de tendencias a longo prazo, estendendo-se por meses e anos, os dados do mercado de açoes podem ser
        considerados como essencialmente estacionarios por um periodo de dias.

Desta forma, podemos explorar a propriedade pseudo-estacionaria de um processo estocastico para estender a utilizade de uma
rede neural, retreinando-a em determinados intervalos regulares, levando em conta assim as flutuaçoes estatisticas dos dados
incidentes. Esta abordagem pode, por exemplo, ser adequada para processar dados do mercado de açoes.
    Para uma abordagem dinamica mais refinada, pode-se proceder como segue:

    *.  Selecione uma janela suficientemente estreita para que os dados de entrada possam ser considerandos
        pseudo-estacionarios e use os dados para treinar a rede.
    *.  Quando for recebida uma nova amostra dos dados, atualize a janela eliminando a amostra de dado mais antiga e deslocando
        as amostras restantes para tras, em uma unidade de tempo, para fazer espaço para a nova amostra.
    *.  Utiliza a janela de dados atualizados para treinar a rede novamente a rede.
    *.  Repita o procedimento de forma continua.

Podemos, assim, incorporar a estrutura temporal no projeto de uma rede neural fazendo com que a rede sofra treinamento
continuado com exemplos ordenados no tempo. De acordo com esta abordagem dinamica, uma rede neural eh vista como um filtro
adaptativo nao-linear que representa uma generalizaçao dos filtros adaptativos lineares. Entretanto, para que esta abordagem
dinamica para filtros adaptativos nao-lineares seja realizavel, os recursos disponiveis devem ser suficientemente rapidos para
completar todos os calculos descritos durante um periodo de amostragem. Somente entao o filtro acompanhara as variaçoes na
entrada.



2.13                                 NATUREZA ESTATISTICA DO PROCESSO DE APRENDIZAGEM

A ultima parte do capitulo trata dos aspectos estatisticos da aprendizagem. Neste contexto, nao estamos interessados na
evoluçao do vetor de pesos 'w' enquanto a rede neurla passa ppor uma lgoritmo de aprendizagem. Em vex disso, concentramo-nos no
desvio entre uma funçao "alvo" 'f(x)' e a funçao "real" 'F(x,w)', realizada pela rede neural, onde o vetor 'x' representa o
sinal de entrada. O desvio eh expresso em termos estatisticos.
    Uma rede neural eh meramente uma forma pela qual conhecimento empirico sobre um fenomeno fisico ou ambiente ou ambiente de
interesse pode ser codificado atraves de treinamento. Por conhecimento "empirico" entendemos um conjunto de medidas que
caracterizam o fenomeo. Para sermos mais especificos, considere o exemplo de um fenomeno estocastico descrito por um vetor
aletorio 'X' consistindo de um conjunto de variaveis independentes, e um escalar aleatorio 'X' podem ter significados fisics
particulares diferentes. A suposiçao de que a variavel dependente 'D' eh escalar foi feita simplismente para simplificar a
exposiçao, sem perda de generalidade. Suponha tambem que tenhamos 'N' realizaçoes do escalar aleatorio 'X' representadas por
{'Xi'}[i=1,N], e um conjunto correspondente de realizaçoes do escalar aleatorio 'D' representado por {'di'}[i=1,N]. Estas
realizaçoes (medidas) constituem a amostra de treinamento representada por

                                                (Eq. 2.53)

Normalmente, nao conhecemos a relaçao funcional exata entre 'X' e 'D' e assim prosseguimos propondo o modelo

                                                (Eq. 2.54)

onde 'f(.)' eh uma funçao deterministica do seu argumento vetorial, e 'e' eh um erro de expectativa aleatorio que representa a
nossa "ignorancia" sobre a dependencia de 'D' e 'X'. O modelo estatistico descrito pela equaçao 2.54 eh denominado um modelo
regressivo; ele esta representado na figura 2.20a. O erro de expectativa 'e' eh, em geral, uma varivel aleatoria com media nula
e probabilidade de ocorrencia positiva. Baseado nisto, o modelo regressivo da figura 2.20a apresenta duas propriedades uteis:

                                                (Fig. 2.20)