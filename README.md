
# Let the CI spot the holes in tested code with the Descartes tool

Bring your laptop, your favorite Java project (with JUnit tests) and find out how much of the covered code is actually specified by the test suite!

In this tutorial, we introduce the intriguing concept of **pseudo-tested** method, i.e., methods that are covered by the test suite, yet no test case fails when the method body is removed. We show that such methods can be found in mature, well-tested projects and we discuss some possible root causes. Attendants have the opportunity to experiment **hands-on with our tool, called [Descartes tool](httsp://github.com/STAMP-project/pitest-descartes)**, which automatically detects pseudo-tested methods in Java projects.

The tutorial is structured in three  parts:
1. Introduce the concept of [pseudo-tested methods](https://arxiv.org/pdf/1611.07163.pdf). We position these methods in the  context of test adequacy assessment and contrast them  with code coverage and mutation testing. We illustrate the concept with  examples found in large, well tested open source projects developed by the Apache foundation, Google,  Amazon and Spotify. 
2. Let the attendants discover the presence of pseudo-tested methods in their own Java projects using our [**Descartes tool**](httsp://github.com/STAMP-project/pitest-descartes). This tool automatically transforms all the methods that are covered by one test case at least into empty methods.  The following code shows an example of a method and the potential transformations that **Descartes** could create:

    ```Java
    //Original method
    public static long factorial(int n) {
        if(n==0) return 0;
        long result = 1;
        for(int i = 2; i <= n; i++)
            result *= i;
        return result;
    }

    //Variant 1
    public static long factorial(int n) {
        return 0;
    }

    //Variant 2
    public static long factorial(int n) {
        return 1;
    }
    ```
    Then the test suite is run on each transformed method, leveraging the mature and efficient transformation and test execution engine of [**PITest**](http://pitest.org/). Attendants will learn how to configure the tool for their projects and interpret the results.
3. We demonstrate the usage of  [**Descartes tool**](httsp://github.com/STAMP-project/pitest-descartes) in a Continuous Integration (**CI**) environment. We show how it can be integrated within Jenkins and Maven to monitor the evolution of a test suite. This last part is also a mix of presentation and hands-on with specific examples taken from XWiki, a well-tested, active Java-based CMS: [1](https://github.com/xwiki/xwiki-commons/blob/master/pom.xml#L120), [2](https://github.com/xwiki/xwiki-commons/blob/master/pom.xml#L2083), [3](https://github.com/xwiki/xwiki-commons/blob/master/pom.xml#L2119), [4](http://ci.xwiki.org/job/xwiki-commons_pitest/).

## Previous talks

This tutorial has never been presented before. Yet, some parts about the presentation of pseudo-tested methods, test adequacy and Descartes have been addressed in previous talks given by the instructors:
* **Advanced testing in action on a Java project**: Vincent Massol gave a version of this talk at [FOSDEM'84](https://fosdem.org/2018/schedule/event/advanced_testing_java/) in front of approx. 100 Java developers and another version at [Devoxx'18](https://cfp.devoxx.fr/2018/talk/OCF-8843/Nouvelle_generation_de_tests_pour_projets_Java)  in front of approx. 800 Java developers. In these talks, Vincent covers aspects related to test quality, test generation and continuous integration. The video for the talk at FOSDEM’18 is publicly [available](http://mirror.onet.pl/pub/mirrors/video.fosdem.org/2018/H.2213/advanced_testing_java.webm). A [chapter](https://lescastcodeurs.com/2018/05/18/lcc-189-conferences-et-tests-par-mutation/) of the LesCastCodeurs podcast also included a discussion about **Descartes** and mutation testing. 
* **Mutate and Test your Tests**: Talk given by Benoit Baudry at [EclipseCon Europe 2017](https://www.eclipsecon.org/europe2017/session/mutate-and-test-your-tests) in front of approx. 60 Java developers and testers. This talk was practically oriented, based on concrete examples that illustrate the concepts of **pseudo-tested** methods and the relation with test suites. The [slides](https://www.slideshare.net/slideshow/embed_code/81650071) and [video](https://www.youtube.com/watch?v=rlfcGUDkSjQ&t=) for this talk are publicly available. They illustrate the type of content that serves as a basis for the tutorial proposed here.

## Instructors
<img src="http://ssbse18.irisa.fr/img/team/oscar.vera.jpg" alt="Oscar L. Vera" width="150" height="150" />

**Oscar Luis Vera Pérez:** PhD Student at Inria Rennes, France since 2017 and member of the [DiverSE research group](https://diverse.irisa.fr/). He has been involved as a lecturer in the course of Software Validation and Verification for master students at the University of Rennes. He received his B.S in Computer Science in 2007 and a M.S degree in Mathematics in 2012 at the University of Havana Cuba where he also taught the subjects of Programming and Compiling. His current research interests are related to software testing, mutation testing and search-based software engineering.

![Vincent Massol](https://forum.xwiki.org//user_avatar/discourse.xwiki.org/vmassol/150/6_1.png)
**[Vincent Massol](https://about.me/vmassol):** CTO of [XWiki SAS](https://www.xwiki.com/fr/) and an active committer of the XWiki open source project. Before being paid to work on open source he spent over 10 years working nights and week ends having fun on various open source projects (committer on Apache Maven, creator of Apache Cactus and Codehaus Cargo to name a few). Vincent also co-authored 3 books: JUnit in Action, Maven: A Developer’s Notebook and Better Builds with Maven. He is a regular speaker at IT and Java conferences and also a member of [LesCastCodeurs podcast](https://lescastcodeurs.com/), a French podcast focusing on news in the Java world at large.

<img src="http://people.rennes.inria.fr/Benoit.Baudry/pics/benoit-baudry-2014.png" alt="Benoit Baudry" width="150" height="150" />

**[Benoit Baudry](https://softwarediversity.eu/):** Professor in software technology at the KTH Royal Institute of Technology (Stockholm, Sweden). Until August 2017 he was a research scientist at INRIA, France, where he led the [DiverSE research group](https://diverse.irisa.fr/) since 2013. His research interests are in the area of automatic software testing, software diversity and DevOps. He has been teaching software testing and automatic software engineering at Universities and companies since 2004. He regularly gives talks in academic and industry conferences.

