---
title: Unit testing for beginners - Part 2
ref: unit2
lang: en
layout: post
author: Carlos Schults
permalink: /en/unit-testing-for-beginners-part2/
img: http://res.cloudinary.com/dz5ppacuo/image/upload/v1459979937/testes-unitarios-iniciantes-min_povcse.png
tags:
- software testing
- unit testing
- automated tests
- agile
---

# Unit Testing For Beginners - Part 2

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1459979937/testes-unitarios-iniciantes-min_povcse.png)

Better late than later! Time to continue our series on unit testing for beginners. Today you're going to write your first unit test.

## Introduction

In the [previous article](http://carlosschults.net/pt/testes-unitarios-iniciantes-parte1) you learned what unit tests are and what are the motivations for writing them.

Today you're going to learn how to create unit tests. I'll show you how to install and use the a unit test framework called **NUnit**. Together, we're going to write some tests in order for you to know some of its features.

## NUnit Installation

If you recall the [previous article](http://carlosschults.net/pt/testes-unitarios-iniciantes-parte1), you'll remember that, in order to write and run unit tests, you need a **unit testing framework.**

The framework we're going to use is **NUnit**, based on **JUnit**, which is a test framerwork for the Java language. There are other testing frameworks available in the .Net world, such as MS Test, developed by Microsoft itself.
Feel free to try other frameworks later on.

Ok, let's begin. For this project I'm going to use Visual Studio 2017. [Download the Community version here](https://www.visualstudio.com/pt-br/downloads/).

Create a new solution of the **Class Library** type, with the name **LearningUnitTesting**.

Whenever I create a new solution on Visual Studio I delete the `Class1` class that is created by default. You could rename it, of course, it makes no difference.

Now, let's rename the default project to **Application**. This project will store the *production code* in our solution.

> In the context of unit testing, we use the term **Production Code** when we're talking about the "real code" in our application, in contrast to the **Test Code** we also write.

Next step! Now we **create the test project**. There are several different opinions regarding *where* should the test class be kept: along with production code, or in a different location. I usually create another project, which I name using the scheme *[ProductionProject]Test*.

So, the new project will be called **ApplicationTest**, and it'll be of type **Class Library** as well.
After creating the project, I delete the default class, same as before.

Your solution should look like this:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498503229/unit2-img1_ugbo3b.png)

Let's install NUnit. Fortunately, NUnit is available as a Nuget package, which makes its installation a breeze.

First, open the **Package Manager Console**. Go to: **Tools** > **Nuget Package Manager** > **Package Manager Console**. 

Then type or copy-paste the following command:

> Install-Package NUnit

Double-check that you've got the right project selected, like in the image:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498503359/unit2-img2_nzedn5.png)

And then press *ENTER*. The installation will be done in a few seconds.

We are not done yet, though. We need to install another package, the **NUnit Test Adapter**, which we'll let us run NUnit tests in Visual Studio. The process is the same, the only difference is the package's name:

> Install-Package NUnit3TestAdapter

Don't forget to check if the right project is selected before pressing *ENTER*. The installation will be done in a few seconds.

This is it.

## Creating and running the first test

Let's create some tests. First, let's add a new class to our production project. The class's name will be `Employee` and its code will look like this:

<script src="https://gist.github.com/carlosschults/3f42e324b10ceb42b360382686d314de.js"></script>

I think the class is simple enough to not require aditional explanation. Now, it's time to create our test class. Add a new class called `EmployeeTest` to the **ApplicationTest** project. 

> This is another naming convention I like to use: to name the test class after the production class, adding the word *Test* at the end. 

After the class is created, add the *NUnit.Framework* namespace to its using declarations. Then, create a new void returning public method called **MyFirstTestMethod** and add the `[Test]` attribute to it.

By now, your code should look like this:

<script src="https://gist.github.com/carlosschults/406525bd23d3ee2ecba4f7592c0f8af3.js"></script>

The skeleton for the test is ready. It's time for you to write your first **assertion**. In the context of unit testing, an assertion is an affirmation about how a unit of your system should behave. If the afirmation turns out to be true, we say the test has *passed*. In case it proves to be false, we say the test has *failed*.

In NUnit we use the `Assert` class to write our assertions. This class has a large number of methods that allow us to express our expectations about the behaviour of our units.

Add the following line of code to the test method:

> Assert.Pass();

The `Pass` method, not surprisingly, just forces the test to pass. Now you're going to run this test in order to see it passing. First of all, open the **Test Explorer**. Use the menu bar: **Test** > **Windows** > **Test Explorer**.

When the window is show, click on *Run All*. If everything goes right, you'll see this:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498507514/MyFirstTestPass_atkrjl.png)

When you click on the test's name, some additional information is shown, such as the test file and elapsed time:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498508050/MyFirstTestPass2_ageqqm.png)

Notice the use of green to indicate the test's success.

Now let's do the opposite: force the test to fail. Replace the previous line for the following one:

> Assert.Fail();

Run the test again and you'll see the failure message, this time with the red bar:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498508371/myfirsttestfail_xwuo5u.png)

Now that you're getting the hang of it, we're start testing our `Employee` class. Don't forget to switch the test method back to `Assert.Pass()`, otherwise it will continue to fail.

Now add a new method called `IntroduceMethodShouldWorkCorrectly`. In this method we'll create a new instance of `Employee` and verify that the `Introduce` method is working properly.

Before we do that, though, we must add a reference from the production project to our test project. Otherwise, our test class won't be able to see the classes it is suposed to test!

To do that, right-click the **ApplicationTest** project, then go to **Add**, then **Reference**. In the opened window, choose the project, according to the following image:

![](http://res.cloudinary.com/dz5ppacuo/image/upload/v1498509304/Captura_de_tela_2017-06-26_17.34.04_hgianj.png)

Then, click on **OK**.

Back to the test class. Edit the code so it looks like this:

<script src="https://gist.github.com/carlosschults/c840590dab95a023d4530962fca048db.js"></script>

You will notice that `Employee` is marked as an error. If you hover over it, you'll see a message saying that the name `Employee` couldn't be found and asking if there is some reference or *using* directive missing.

Of course there is a using directive missing, related to the reference we've just added. To fix this problem, just add the line `using Application;` to the namespace declarations, right at the start of the file.

Now that our code compiles, let's go through this method, line by line.

In the first line, we create a new instance of `Employee`, specifying name, profession and salary. In the following line, we assign to a variable the value we **expect** the method to return. Then we assign to another variable the obtained result from the method.

Finally, we use the `AreEqual` method from the `Assert` class to verify the equality of the two values. This method is, probably, the one you'll use the most during your tests.

Now it's time to run the test. Use the shortcut **CTRL + R, A** or click on **Run All** in the Test Explorer window. If everything goes smoothly, you should see the green bar and the message indicating that both tests have passed.

Time to test our test! We're going to deliberately ruin the `Introduce` method to see if the test fails as expected. Back to the production class, edit the method like this:

<script src="https://gist.github.com/carlosschults/02554ca9b8dd69f8c904dbbcc271c99e.js"></script>

As you've seen, we've just removed the square brackets before and after "JobTitle". This way, the string interpolation won't work, hardcoding the string instead of replacing it by the value of the variable.

When we run the tests again, we got the following result:

> Mensagem:   Expected string length 48 but was 46. Strings differ at index 37.
Expected: "Hi! My name is Alice and I work as a Programmer."
But was:  "Hi! My name is Alice and I work as a JobTitle."
------------------------------------------------^

As you can see, the message is very detailed. It not only lets us know that the strings differed, but it also tells us exactly where they differ. It also shows the expected string and what we really got. It is important to notice that the parameter's orders in the `AreEqual` matters a lot, since it is used in the failure message.
  
> **The parameters' order in the `AreEqual` is very important. First specify the expected value, and then the actual result.**
  
Great. Now you can switch the method back to the correct implementation and run the tests again, so the test can be green again.

As you can see, a unit test consists in a well defined sequence of steps: we **prepare** the scenario, then **execute** the action and **verify** the results. This sequence of steps, or phases, is sometimes called AAA: **Arrange-Act-Assert**.
  
> A tipical unit test has the three phases: **Arrange-Act-Assert**.

Even though there are another naming conventions for the phases of a unit test, we'll adopt **Arrange-Act-Assert** , at least for now.

You may be wondering why I gave the name "sut" to the variable at the start of the method. This is a naming convention that I learned while reading [Mark Seeman's blog](http://blog.ploeh.dk/). **SUT** stands for *System Under Test*, i.e. the thing you're testing.

There is nothing preventing you from naming the variable whatever you want. I really like to follow this convention, though, since it makes really clear what is being tested.

> **Tip: Try to use naming conventions that improve the readability of your code and make the author's intention clear for anyone who reads the code.**
  
Take a look at the same test method, but this time with comments delimiting each test phase:
  
<script src="https://gist.github.com/carlosschults/a91d41ff7ac732fc9c57e63c03a6be07.js"></script>
  
Even though it isn't really need, I suggest you use comments like the ones above to indicate the test phases, at least in the beginning of your learning.
  
## Testing the `GiveRaise` method
  
A salary raise is always welcome, wouldn't you agree? Let's test the `GiveRaise` method to see if it's working properly. Add the following method to your test class:

<script src="https://gist.github.com/carlosschults/2ce153c1da6f83e80342fa7f83ea4786.js"></script>

Run the test and you should see the familiar green bar. Did it work? Great. Time to **test the test**: we're going to sabotage the implementation of `GiveRaise` and hope our test catches the error.

In the production class, edit the method this way:

<script src="https://gist.github.com/carlosschults/fba5901aaa2f542bcd8528de0e96afff.js"></script>

Now the method is obviously wrong; the test should fail. Let's run it?

 > Mensagem:   Expected: 110
   But was:  5m
  
Ok, as we can see, the test did fail. Switch the method back to the correct implementation.

## A last test

Let's say the Product Owner just showed up with a new requirement: the `GiveRaise` method should ignore negative raise rates. First, let's edit the `GiveRaise` method to deal with this scenario:

<script src="https://gist.github.com/carlosschults/3f09a8043a1e58753adf9bfdee37350a.js"></script>

We've just made a change in production code. Our top priority right now is **to guarantee that we haven't broken anything**.
Run the test to be sure that all of them are passing.

Everything still green? Great, let's go ahead. Agora precisamos criar um novo teste para documentar o caso da tentativa de aumento negativo.

> Testes de unidade também são uma forma de documentação.

Na classe de teste, adicione o método a seguir:

<script src="https://gist.github.com/carlosschults/a474698655450da6547dbfa6b9dbcb8c.js"></script>

Nada de surpreendente aqui, certo? À esta altura, você já deve ter pegado o jeito da coisa. Assim, vou deixar por sua conta o **teste do teste:** sabote o método de uma ou mais maneiras e confira que o teste falhou conforme deveria.

## Recapitulando

O artigo de hoje foi bem mais prático que o anterior. Conseguimos abordar diversos tópicos:

- Instalação do **NUnit** e **NUnit Test Adapter**;
- Criação de caso de teste;
- Conceito de *asserção* e classe `Assert`;
- Execução dos testes, tanto por meio do *Gerenciador de Testes* quanto por teclas de atalho;
- Interpretação da mensagem de erro do teste;
- Fases do teste unitário (*Arrange-Act-Assert*).

Além desses tópicos, também ampliamos nosso vocabulário relativo à testes, com os termos *SUT*, *asserção*, *código de teste x código de produção*, entre outros.

Também foram abordados alguns padrões de nomenclatura, tanto para classes quanto para métodos de teste.

Finalmente, você aprendeu sobre a importância de ver o teste falhar, e como podemos "testar o teste" através de uma sabotagem deliberada do código de produção.

## Conclusão

Este foi o segundo artigo da minha série sobre testes unitários. Como já mencionei, ele é propositalmente maior e mais prático que o artigo inicial da série. Ainda assim, tudo o que foi abordado é apenas a ponta do iceberg do que existe a respeito de testes de unidade. Livros inteiros poderiam foram escritos sobre este assunto. Nos artigos futuros indicarei alguns, além de outros materiais para estudo.

Nos testes que escrevemos hoje, utilizamos a abordagem mais intuitiva - e provavelmente mais comum - de se criar os testes após o código de produção. Porém, muitas pessoas e equipes trabalham com uma metodologia diferente: eles escrevem os testes *antes* do código de produção.

Pode parecer estranho, à princípio, mas trabalhar desta forma pode trazer diversos benefícios para seu projeto. Este e outros tópicos serão abordados no próximo artigo.

Até lá!
