---
title: "Escrevendo código bom: como reduzir a carga cognitiva do seu código"
ref: codigo-bom
lang: pt
layout: post
author: Carlos Schults
permalink: /pt/escrevendo-codigo-bom/
img: https://res.cloudinary.com/dz5ppacuo/image/upload/v1490471059/escrevendo-codigo-bom-1038x437_e4oy0i.jpg
tags:
- traducoes
- boas-praticas
---

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490471059/escrevendo-codigo-bom-1038x437_e4oy0i.jpg)

**NOTA**: O artigo a seguir foi originalmente escrito por [Christian Maioli M.](https://chrismm.com/), que gentilmente me autorizou a fazer esta tradução. Caso seja do seu interesse, [confira o artigo original](https://chrismm.com/blog/writing-good-code-reduce-the-cognitive-load/).

<!--more-->
----
<p></p>

Baixo número de bugs, boa performance, facilidade de modificação. Código bem feito gera alto impacto, e talvez seja a maior razão por trás da existência do famoso desenvolvedor "10x". E ainda assim, apesar de sua importância, código bom escapa a novos desenvolvedores. A literatura nessa área geralmente consistente de coleções de dicas desconexas. Como um novo desenvolvedor vai simplesmente memorizar isso tudo?  “[Code Complete](https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670/ref=as_li_ss_tl?ie=UTF8&linkCode=ll1&tag=chrimaiospo06-20&linkId=6aabd46b91da513d86257af2c05b6585)“, o maior expoente nesta matéria, é um livro de 960 páginas!

**Eu acredito que é possível construir um framework mental simples que pode ser usado com qualquer linguagem ou biblioteca e que vai resultar em código de boa qualidade por padrão.** Há cinco conceitos principais sobre os quais vou falar aqui. Basta mantê-los em mente e escrever código de boa qualidade será moleza.

Update: Mia Li fez a gentileza de disponibilizar uma tradução deste artigo para o Chinês [aqui](https://www.inside.com.tw/2016/07/05/writing-good-code-how-to-reduce-the-cognitive-load-of-your-code).

## Mantenha suas peculiaridades pessoais de fora

Você lê um artigo que explode a sua mente com truques novos. Agora você vai escrever código "esperto" e todos os seus colegas ficarão impressionados.

O problema é que as pessoas só querem corrigir seus bugs e ir em frente. Seu truquezinho esperto é, com frequência, pouco mais que uma distração. Como eu falei em "[Applying neuroscience to software development](https://chrismm.com/blog/applying-neuroscience-to-software-development/)“, quando as pessoas têm que digerir  seu código, as “pilhas mentais" enchem depressa e se torna difícil fazer progresso.

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490470570/image_0_fzqyo8.png)

<figcaption>Não personalize seu trabalho em maneiras que irão precisar de explicações. 

Tradução do comentário: Isso era útil na linguagem C para evitar escrever acidentalmente "variable = null". Atualmente, isso apenas confundiria a maioria das pessoas, com pouco benefício.</figcaption>
<p>&nbsp;</p>

Não codifique "do seu jeito". Apenas siga a padronização de código. Este tipo de coisa é um problema já resolvido. Torne seu código previsível e fácil de ler codificando da maneira que as pessoas esperam.

## Dividir para conquistar

Código complexo frequentemente pode ser clarificado por meio da modularização, e existem mais maneiras de se fazer isso do que apenas criando mais funções. Gravar o resultado de longas condicionais em uma variável ou duas é uma grande maneira de modularizar sem o overhead de chamar uma função. Isso irá inclusive lhe permitir compô-las em condicionais maiores, ou reutilizar o resultado em algum outro lugar.

**A abordagem ao se dividir um problema deve ser tornar cada seção o mais focada possível, afetando apenas estado local, sem misturar com assuntos irrelevantes, e se possível sem nenhum efeito colateral.** Linguagens de programação e bibliotecas muitas vezes têm seus próprios problemas, e abstraí-los pode ajudar a fazer com que seu código cuide apenas dos assuntos dele. O [Princípio da Responsabilidade Única](https://code.tutsplus.com/tutorials/solid-part-1-the-single-responsibility-principle--net-36074) é outro exemplo de como código focado e localizado resulta em bom design.

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490470570/image_1_rfmnyv.png)

<figcaption>Eu gosto de utilizar variáveis para compartimentar lógica.
Tradução do comentário: Isso pode ser uma boa maneira para modularizar sem o peso excessivo de chamadas de funções</figcaption>
<p>&nbsp;</p>

TDD, além de trazer seus próprios benefícios quando feito corretamente, tem feitos com que as pessoas apliquem certos princípios que anteriormente não eram tão populares. Código sem estado era desprezado como lento e desnecessário (ver: maior parte de código antigo em C/C++), e agora todos estão falando sobre funções puras. Mesmo que você não use TDD, você deveria aprender seus princípios. Trabalhar sob novos paradigmas transformará você em um desenvolvedor resiliente.

## Torne seu código discreto e processável

Seu computador e suas ferramentas podem sofrer tanto quanto você para lidar com seu código, e existe alguma correlação entre o número de pré-processadores e mutações você precisa aplicar e o quão bagunçado o seu código é.

Vamos deixar de lado os possíveis benefícios destas ferramentas de build adicional por um momento. A probabilidade é de que elas requerem que você use linguagens de domínio específica como templates customizados, ou estruturas de dados dinâmicas e complexas como hash tables. A sua IDE provavelmente não será boa em lidar com tais coisas, e a localização de trechos relevantes do código se tornará mais difícil.

Evite usar extensões de linguagens e bibliotecas que não trabalham bem com sua IDE. O impacto que eles terão na sua produtividade bate de longe o pequeno benefício de uma configuração mais fácil ou a economia de algumas poucas teclas com uma sintaxe mais concisa.

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490470570/image_2_pn1dp4.png)

<figcaption>
O uso de Service Locator é um exemplo de design que resulta em integração ruim com a maioria das IDEs.
Tradução do comentário: Uso de string mágicas fará com que seja impossível para sua IDE acompanhar seu código.
</figcaption>
<p>&nbsp;</p>

Outra maneira de manter a parte "integrada" da sua IDE relevante é evitar código mágico. A maioria das linguagens disponibilizam maneiras para que você escreva código mais dinâmico. Abusar tais features utilizando strings mágicas, índices de arrays mágicos e funcionalidades de templates customizados irá resultar em uma base de código mais desconectada. Geralmente qualquer feature que apenas um humano sabe o significado vai levar você para essa caminho, e é uma estrada difícil de se escapar, porque se a sua IDE não entende o código, quaisquer funcionalidades de refatoração que possua serão inúteis quando você quiser mudar para uma arquitetura mais estática.

## Torne seu código legível

Trabalhe no sentido de ter uma arquitetura previsível. Seus colegas de time terão mais facilidade em localizar as coisas, e isso vai reduzir bastante o tempo necessário para concluir as tarefas. **Assim que vocês estiverem de acordo sobre uma estrutura arquitetural geral para seu projeto, torne óbvia a localização dos principais elementos.** Usa MVC? Coloque models, views e controllers em suas próprias pastas, não três níveis abaixo ou espalhados em vários lugares.

Eu falei sobre modularização. Também é possível existir modularização em excesso, o que geralmente torna seu código mais difícil de localizar. Sua IDE pode oferecer alguma ajuda, mas às vezes você estará dividido entre fazer com que sua IDE ignore uma pasta de biblioteca ou outro terceiro devido a ela conter muito código irrelevante, ou mantê-la indexada e lidar com o problema manualmente. É um beco sem saída. Tente utilizar menos bibliotecas escolhendo aquelas que resolvem tantas necessidades quantas forem possível.

Bibliotecas e ferramentas também podem ser uma barreira a novos desenvolvedores. Eu recentemente fiz um projeto usando EcmaScript 7 (babel), apenas para depois perceber que nosso desenvolvedor júnior estava tendo problemas para entender o que tudo aquilo significava.  Uma penalidade pesada para a produtividade do time. Eu subestimei o potencial daquilo de sobrecarregar uma pessoa que está só começando. Não use ferramentas que ainda são difíceis demais de aprender. Espere por uma época melhor.

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490470570/image_3_vdvcrz.png)
<figcaption>Código real de um makefile que escrevi. Desenvolvedores juniores não conseguem lidar com o uso excessivo de novas ferramentas.</figcaption><p>&nbsp;</p>

## Torne seu código fácil de digerir

Se você chegou até aqui, eu tenho boas notícias: esta é provavelmente a parte mais importante. A escolha de bons nomes é sabidamente um dos maiores problemas no desenvolvimento de software. Ferramentas de build provavelmente não vão causar nenhuma melhora aqui, e a razão é que computadores não podem realmente saber o raciocínio que houve por trás de uma solução.

**Você precisa documentar o porquê. Nomes de variáveis e funções relevantes e contextuais são uma ótima maneira de se fazer isso.** Nomes que transmitem propósito podem até reduzir a necessidade de documentação.

O uso de prefixos em nomes é uma boa maneira de adicionar sentido a eles. É uma prática que costumava ser popular, e eu penso que o mau uso foi o motivo dela não continuar a ser usada. Sistemas de prefixos como  [notação húngara](https://www.joelonsoftware.com/articles/Wrong.html) inicialmente tinham a intenção de adicionar sentido, mas com o tempo eles acabaram sendo usado em maneiras menos contextuais, tais como para adicionar informação de tipo.

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1490470570/image_4_x8oly3.png)
<figcaption>Interfaces fluentes tem sido abusadas frequentemente em tempos recentes.</figcaption>
Tradução do comentário: Use nomes que transmitam propósito, não tome vantagem da linguagem apenas para parecer inteligente

Finalmente, sempre há algo a ser dito sobre manter a complexidade ciclomática baixa. Isso significa manter o número de ramificações condicionais tão baixo quanto for possível. Cada ramificação adicional não apenas adiciona mais indentação e prejudica a legibilidade, mas, mais importante que isso, aumenta o número de elementos aos quais você precisa estar atento.

## Conclusão e mais leituras

Estes são cinco conceitos simples e abrangentes, e o meu objetivo aqui foi tornar seu aprendizado mais fácil ao lhe dar caixas nas quais colocar todas as suas ideias sobre organização de código.

**Pratique focar nesses aspectos ao programar para solidifica-los.** Se você ainda não leu, eu realmente recomendo Code Complete. Ele vem com um grande número de exemplos e disseca quase todas as situações que você pode vir a encontrar.
