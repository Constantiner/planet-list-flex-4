# planet-list-flex-4

A legacy Adobe Flex 4 project was created in May 2010 (to preserve code on GitHub).

Flex 4 introduces separating containers and their layouts. This flexible feature is excellent for creating customized versions of standard data controls (for example, `List`). So we can control it with a different look and feel and represent our application as an ordinal list (from the developer's perspective). We can even switch between `List` representations using the new Flex 4 states syntax with rich and impressive GUI and the same application logic.

This project illustrates these conceptions using the Solar System's planets. It offers natural planet representation with all the List capabilities.

Another great advantage of the new Flex layout architecture is the possibility to use unit testing for layouts without creating visual components. New architecture increases testability, which is illustrated in the source code.

[Wayback Machine](https://web.archive.org/) archived [the original article from my blog](https://web.archive.org/web/20100827162214/http://riapriority.com/en/blogs/index.php/constantiner/custom-layout-solar-list-flex4).

## How to build

### Flash Builder 4

See `pom.xml` for required versions. This project can built successfully using `Flex SDK 4.0.0.14159`. The main source folder should be `src/main/flex`. Also, you should add `src/main/resources` and `src/test/flex` (if you plan to run unit tests).

The additional compiler options are the following:

```bash
-locale en_US -allow-source-path-overlap=true -source-path=locale/{locale}
```

If you want to run tests you should add `ASMock 1.0RC` (you can download it [here](http://asmock.sourceforge.net/)). [The required bundle](http://sourceforge.net/projects/asmock/files/asmock/asmock-1.0rc/asmock-1.0rc.zip/download) is ASMock with FlexUnit 4 integration, containing two required `swc` files.

### Maven with Flex Mojos

Run:

```bash
mvn package
```

Do not forget to comment out `maven-default-http-blocker` mirror setting in Maven's `settings.xml`.

Add [the following repository](http://repository.sonatype.org/content/groups/flexgroup/) to Maven's `settings.xml` or the Nexus as a proxy repository
(see more details [here](http://www.sonatype.com/books/mvnref-book/reference/installation-sect-details.html#installation-sect-user)).

Because of problems with running tests with custom runner (`[RunWith]` metatag) unit tests can't be run with Flex Mojos. So, tests are skipped, and all the required dependencies are commented on. Will try to resolve this issue in the future.

## Thanks

Special thanks to [Evtim Georgiev](http://evtimmy.com/) for some ideas on implementation and [Chet Haase](http://graphics-geek.blogspot.com/) 
and his [Flex 4 Fun book](http://www.artima.com/shop/flex_4_fun) for additional information about animations.
