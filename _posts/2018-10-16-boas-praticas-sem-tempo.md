---
title: "Boas Práticas De Programação Para Os Apressados"
ref: best-practices-short-time
lang: pt
layout: post
author: Carlos Schults
description: No post de hoje eu falo de algumas boas práticas de programação que podem aumentar a qualidade da sua aplicação em pouco tempo.
permalink: /pt/boas-praticas-sem-tempo/
img: https://res.cloudinary.com/dz5ppacuo/image/upload/v1539703469/coding-best-practices-1038x437_ugnhab.jpg
tags:
- csharp
- boas praticas
---

![](https://res.cloudinary.com/dz5ppacuo/image/upload/v1539703469/coding-best-practices-1038x437_ugnhab.jpg)
Photo by Ales Nesetril on Unsplash


*NOTA: Este post foi originalmente escrito para o blog da the SubMain.  Você pode [ler o artigo original no site deles, em inglês](https://blog.submain.com/coding-best-practices-short-time/). Quando estiver por lá, baixe e experimente o CodeIt.Right.*

Um dos tópicos em desenvolvimento de software que me interessa muito são boas práticas de codificação. Eu estou sempre pesquisando e buscando maneiras de aperfeiçoar meu trabalho e entregar valor de forma rápida e consistente.

Pode ser meio espinhoso definir o que "[é realmente uma boa prática"](https://www.daedtech.com/what-is-a-best-practice-in-software-development/). Há pessoas que inclusive sugerem [aposentar o termo!](https://dzone.com/articles/death-best-practices) Mas um ponto em que praticamente todos concordam é: descobrir e implementar estratégias - não importa o nome que você coloca nelas - para melhorar o resultado do seu trabalho é algo que qualquer programadora ou programador que faz jus a esse nome deveria fazer continuamente. 

Claro, não existe almoço grátis. A adoção de uma boa prática leva tempo, o que você provavelmente não tem muito sobrando para começo de conversa. Isso sem mencionar a gerência, nem sempre muito animados a tentarem coisas novas.

Então, o que fazer se a sua equipe de desenvolvimento está sofrendo com a baixa qualidade de uma base de código, mas não tem tempo para implementar as boas práticas que remediariam a situação?

A resposta que eu ofereço é o que eu vou chamar de "pacote emergencial de boas práticas": uma pequena lista de boas práticas de programação que você pode adotar em relativamente pouco tempo para levar sua equipe e sua aplicação do completo caos para um estado mais gerenciável.

Sim, eu sei que há tantos conselhos sobre boas práticas por aí que é até difícil não se sentir sobrecarregado. Por causa disso, eu restringi a minha lista de boas práticas a itens que atendam aos seguintes critérios:

- As boas práticas precisam ser fundamentais, no sentido de que elas são blocos básicos a partir dos quais você pode implementar práticas mais sofisticadas depois.
- Você pode adotá-las em relativamente pouco tempo. (Eu diria que uma semana é praticável.)
- O seu custo é zero ou perto disso.

As práticas a seguir atendem os critérios listados. E sem mais enrolação, aqui está: meu pacote emergencial de boas práticas de codificação, com itens listados na ordem que eles deveriam ser adotados, começando pelo mais crítico.

## Sistema de Controle de Versão

Eu trabalhei uma vez em uma empresa de desenvolvimento de software na qual nenhum sistema de controle de versão era usado. Os arquivos de código fonte ficavam em uma pasta compartilhada que qualquer desenvolvedor podia acessar. Qual era o processo usado para poder editar um arquivo? Você provavelmente adivinhou: nós criávamos uma cópia do arquivo e adicionávamos "_OLD" ao final do nome. 

Isso aconteceu há oito ou nove anos, o que significa que as coisas devem ter melhorado, certo? Bom, provavelmente melhoraram, um pouco, mas não totalmente. Ainda tem [empresas por aí que não usam controle de versão](https://twitter.com/_m_b_j_/status/938785388268806146).

### Como proceder?

From now on, I'll just assume you agree that a VCS is a fundamental coding best practice. If that's not the case, there's plenty of resources out there explaining [what a VCS is](https://www.git-tower.com/learn/git/ebook/en/desktop-gui/basics/what-is-version-control#start) and [why should you use one.](https://www.atlassian.com/git/tutorials/what-is-version-control#benefits-of-version-control)

With that out of the way, it's time to get to specifics. Which tool should you use? How to go about its adoption?

[Git](https://git-scm.com/) is a solid choice. And despite having a steeper learning curve for [those more used to centralized version control systems, such as Subversion or TFVC](http://carlosschults.net/en/git-basics-for-tfs-users), it's *de facto* standard in our industry. So by all means, learn it, since not doing so can harm your career in the future.

But it's possible that Git is not the best choice for your team **right now**. Remember, you're short on time. So we need to get your team to adopt these coding best practices ASAP.

How do we do this? So, let's say you have experience with [Subversion](https://subversion.apache.org/), having used it at your previous company, but you have no experience with Git at all. If that's the case, I'd say Subversion is the best choice for you. The overhead of learning a new system and teaching it to your co-workers while putting it into production would be too great.

## Code Review


I'm not going to lie: I *love *code reviews---and [I'm not alone in that](http://www.codinghorror.com/blog/archives/000495.html). I've witnessed firsthand how a good code review can reduce the number of bugs in a codebase, make the code look and feel more consistent, and perhaps best of all, spread knowledge throughout a development team.

And here's a major selling point: a code review practice is relatively easy to implement. Start as simple as you can, and then tweak and experiment with your approach as the need arises.

### What Do I Mean by Code Review?

Talking about "code review" can be tricky. People sometimes mean widely different things when they use the term, so I think it warrants further clarification.

I'm not in favor of a highly stressful and bureaucratic code review process, where your code is scrutinized and criticized in public for hours. I don't believe in public shaming as a tool for achieving quality. On the contrary, [the type of code review I advocate for](https://blog.submain.com/code-review-vs-pair-programming-2/) is a lightweight and low-stress process, usually initiated by submitting a pull request or using your favorite IDE.

### How to Proceed 

Since we're now on the same page about what a code review should look like, how would one go about implementing the practice? My answer is, not surprisingly, "the simplest way that could possibly work." 

For instance, if yours is a .NET shop using TFS/TFVC, you can start by [installing a check-in policy](https://marketplace.visualstudio.com/items?itemName=ColinD.ColinsALMCheckinPoliciesVS2017) that requires a code review for each check-in. If your team uses GitHub, you can use [pull requests](https://help.github.com/articles/about-pull-requests/). Just start performing reviews so you and your team can get used to it. Then, with time, start tuning and perfecting your approach.

Here are some of the questions that can appear as you refine your process for this:

-   **What's the goal of a code review?** Are we looking for bugs? Trying to improve readability? Checking adherence to the company's coding standard?
-   **Where do we draw the line between "suggestions" and "impediments"?** Is it OK to give a thumbs-down to someone's code for bad indentation or a slightly off variable name?
-   **What do when reviewer and reviewee can't come to a consensus?** Bring in a mediator to give the final word? And who should be this mediator? The lead developer?

The answer to all of these questions can be found in **automation**. Much of the awkwardness of a code review can be removed when you employ a [code analyzer](https://blog.submain.com/different-styles-code-analyzer/) to handle the automatable portions of the process.

For instance, [SubMain's CodeIt.Right](https://submain.com/codeit.right/features) will give you real-time feedback from inside Visual Studio, alerting you of possible coding issues and even automatically fix code smells and violations for you.

By employing automation, you set your developers free to worry about higher level concerns when performing reviews, such as code clarity or architectural decisions.

## Automated Builds


You may be thinking that I've got it wrong. After all, does it even make sense to talk about automated builds without mentioning automated tests?

Well, I'm going argue that yes, it does make sense, and for one very simple reason: it eliminates "[it works on my machine](https://blog.codinghorror.com/the-works-on-my-machine-certification-program/)" syndrome. 

By having a central place where builds are performed, you shed light on all kinds of problems, from poor management of dependencies to bad test discipline.

### How to Proceed

My advice here is the same as before: do the simplest thing that could work.

If your team already uses TFS, then learn how to create a [build definition and you're good to go](https://docs.microsoft.com/en-us/vsts/build-release/actions/ci-cd-part-1). On the other hand, if you host your projects on GitHub, you might be interested in taking a look at [Travis CI.](https://travis-ci.org/)

With time, you should improve your strategy. Remember the static code analyzers I mentioned earlier? You can integrate them into your build process. Unit testing and other kinds of automated tests are a very important addition as well.

Speaking of which...

## Notable Absences

You might be surprised to see that I haven't included unit testing in the list of coding best practices, [despite being myself a firm believer in the importance of automated testing](http://carlosschults.net/en/unit-testing-for-beginners-part1/) to the overall quality of a codebase. And why is that?

Adding unit tests to a legacy application, unfortunately, is *hard*, to the point that there's even [a famous book](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052/ref=sr_1_1?ie=UTF8&qid=1515443597&sr=8-1&keywords=working+effectively+with+legacy+code)that focuses solely on this. It's just not a feasible task for you to tackle quickly.

In a similar fashion, it's possible that a portion of readers expected me to talk about clean code or the [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))principles. I do encourage you to research and learn about these topics,  but I don't think they're a good fit for the purpose of this post. They are, as the name already points out, principles. Think of them as philosophical guidelines---useful, but not as easy to break down into simple, actionable advice.

## Deploy Your Package ASAP!

It's possible that some of you found these practices to be extremely basic and not post-worthy. "Who doesn't use version control in twenty-freaking-eighteen???" I hear you saying.

Well, it really doesn't take long to find evidence (anecdotal, but still) that [things are not all sunshine and rainbows](http://softwareengineering.stackexchange.com/questions/65931/are-there-serious-companies-that-dont-use-version-control-and-continuous-integr). To believe that even basic coding best practices, such as using version control or automated testing, are universally applied is probably more wishful thinking than what we'd like to believe.

For the rest of you, I hope this list proves useful.

You know what they say. "When in a hole, stop digging." And that's exactly the type of help I wanted to offer with this post: a quick and easy fix, meant to give you and your teammates just enough sanity that you can focus and regain control of your application, ensuring its long-term health.