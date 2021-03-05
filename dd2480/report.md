# Report for assignment 4

## ProjectName: [Guava](https://github.com/google/guava)

Description from their project:


> Guava is a set of core Java libraries from Google that includes new collection types (such as multimap and multiset), immutable collections, a graph library, and utilities for concurrency, I/O, hashing, caching, primitives, strings, and more! It is widely used on most Java projects within Google, and widely used by many other companies as well.


## Onboarding experience
>> Did you choose a new project or continue on the previous one?
>> If you changed the project, how did your experience differ from before?

We changed the project to [Google’s Guava](https://github.com/google/guava) from [Termux](https://github.com/termux). We decided to do this because to be able to resolve issues in the previous assignment we needed expertise in Android which none of us had. We decided to go for Guava since the project is purely Java and did not require as much domain knowledge. The issues also seemed easier as well.

There was some communication with the maintainers which impacted which issues we worked on. Initially, we wanted to work on [this issue](https://github.com/google/guava/issues/5388). However, when we communicated with the maintainers they indicated that it was not really a coding issue but rather it had to do with documentation, and so we decided to change to another issue.

[This](https://github.com/google/guava/issues/5372) was the new issue we chose. We communicated with the maintainers and they said that it was not the easiest issue to work on for beginners. We decided, however, to give it a try and possibly contribute with a partial solution or “patch” that at least solves the issue with the test case provided by [William1104](https://github.com/William1104) (the creator of the issue).

The overall onboarding was easier. We initially forked the repo then we cloned it. We ran `mvn verify` and `mvn test`. We noticed that the tests failed. This was because we did not have the correct version of Java. The project-based itself on Java 8 and we all used Java 15. Once we installed Java 8 and changed the `JAVA_HOME` path variable we were able to run the tests. There was only one single test that failed:

```
Failed tests: 
testJarFileWithSpaces(com.google.common.reflect.ClassPathTest): value of: getTopLevelClasses()
```
(for full details on tests, before and after, see [Test results](#test-results).

This test was related to an android test, so we decided that the test would not impact the issue that we would be working on. This concluded the onboarding since the tests ran with only a minor exception.

There were some onboarding issues regarding how to contribute to the project. If you look at the readme it mostly explains how to use the project and less about how to contribute which made it harder to know if we did the onboarding correctly or if there was some convention we should have followed.

## Effort spent
>> For each team member, how much time was spent in
>> 1. plenary discussions/meetings;
>> 2. discussions within parts of the group;
>> 3. reading documentation;
>> 4. configuration and setup;
>> 5. analyzing code/output;
>> 6. writing documentation;
>> 7. writing code;
>> 8. running code?
>> For setting up tools and libraries (step 4), enumerate all dependencies you took care of and where you spent your time, if that time exceeds 30 minutes.

[Link to Andreas’ log book](https://docs.google.com/document/d/1OZsjMdH_ppJU72kHMfrgS7PO7WUo6HUFv6ujeiKdi5E/edit?usp=sharing)</br>
[Link to Axel’s log book](https://docs.google.com/document/d/13l8DoYcv7jKFH0Vujod18wp6Q88Kw9efTzjfDmGxASk/edit?usp=sharing)</br>
[Link to Taqui’s log book](https://docs.google.com/document/d/1H5bNKT5r8lJACJ4CnDGRqnWz6zWudV0phNIk8eIEWvI/edit?usp=sharing)</br>
[Link to Yannis’s log book](https://docs.google.com/document/d/1zTKMO_6bLzeEWNbbSPKQMBnQs8BoDphy1V4oTGs0_ns/edit?usp=sharing)</br>
[Link to Telo’s log book]()

## Overview of issue(s) and work done

Title: Allow RateLimiter users to specify burst behavior</br>
URL: https://github.com/google/guava/issues/5372</br>
TODO: Summary in one or two sentences</br>
TODO: Scope (functionality and code affected).

## Requirements affected by functionality being refactored

>> Optional (point 3): trace tests to requirements.

| **ID**  | **Relevant tests** | **Title**                                                                       | **Description**                                                                                                                                                                                                                                                                         |
| --------|--------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| R1 	    | ***TODO***         | Allow RateLimiter users to specify burst behavior (max burst seconds)           | [Currently](https://github.com/google/guava/blob/e5b5bc42c8c5dfe7c77a64726bf0df07c6fc40c3/guava/src/com/google/common/util/concurrent/RateLimiter.java#L134), the maxBurstSeconds is always set to 1.0. By passing additional parameters, we could allow users to specify this instead. |


## Project plan

_Written on Tuesday 2/3_</br>
For testing, we will first try to use the test provided in the issue. After that we will come up with at least 2-3 more test cases, and make sure they fail before fixing the issue.

To fix the issue, we are preliminarily adding a parameter for maxBurstSeconds and then we will run the tests to see if they pass.

If this turns out to be easy, we will see if there are other parameters we can “customize” (so to speak).

## Code changes

### Patch
>> (copy your changes or the add git command to show them)</br>
>> git diff …</br>
>> Optional (point 4): the patch is clean.</br>
>> Optional (point 5): considered for acceptance (passes all automated checks).

## Test results

Overall results with link to a copy or excerpt of the logs (before/after refactoring).</br>
Before: TODO: Insert link to full log (tiny snippet below)</br>
Results: TODO: insert link to full log</br>

Before:
The only test that failed is correlated to an android specific test. Since the issue we are working on is not related to android we believe that this test fail will not impact our work.
```
Failed tests: 
  testJarFileWithSpaces(com.google.common.reflect.ClassPathTest): value of: getTopLevelClasses()

Tests run: 858390, Failures: 1, Errors: 0, Skipped: 515

[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for Guava Maven Parent HEAD-jre-SNAPSHOT:
[INFO] 
[INFO] Guava Maven Parent ................................. SUCCESS [  0.968 s]
[INFO] Guava: Google Core Libraries for Java .............. SUCCESS [ 16.871 s]
[INFO] Guava BOM .......................................... SUCCESS [  0.086 s]
[INFO] Guava Testing Library .............................. SUCCESS [02:06 min]
[INFO] Guava Unit Tests ................................... FAILURE [09:46 min]
[INFO] Guava GWT compatible libs .......................... SKIPPED
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  12:11 min
[INFO] Finished at: 2021-03-02T10:35:08+01:00
[INFO] ------------------------------------------------------------------------
```


## UML class diagram and its description
text

### Key changes/classes affected
>> Optional (point 1): Architectural overview.</br>
>> Optional (point 2): relation to design pattern(s).</br>

## Overall experience
>> What are your main take-aways from this project? What did you learn?</br>
>> How did you grow as a team, using the Essence standard to evaluate yourself?</br>
>> Optional (point 6): How would you put your work in context with best software engineering practice?</br>
>> Optional (point 7): Is there something special you want to mention here?

[Link to Essence reflection](https://docs.google.com/document/d/1KQ4pNqrz04qa5X6lS0pwcGrY_X-ajNPmXTJFTWebimA/edit?usp=sharing)