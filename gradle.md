# To Create new project use **gradle init**

# To check the tasks **gradle tasks or gradle tasks --all**

# To run the task do **gradle firstTask or gradle fT**

### To change the name of project

**change name in settings.gradle**
<br/>

<h1>Scopes of Maven are known as Configurations in Gradle</h1>
1. implementation <br/>
2. compileOnly<br/>
3. reuntimeOnly<br/>
4. testImplementation<br/>
5. testCompileOnly<br/>
6. testRuntimeOnly<br/>
7. api<br/>

<br/>
<h1>Phases of Gradle </h1>  
1. Initialization --- checks what kindof project its <br/>
2. Configuration -- checks the task required for build<br/>
3. Execution doFirst() and doLast()<br/>
<br/>
<h1>Groovy</h1>
1. Data types: simialar to java (def for var) <br/>
2. pattern operator ~

```groovy
c={ n=6->
    println('hi');
}
c.call(10)
4.times{n-> println n}
4.times{println it}
l = [1,2,3]
l << 4
l = l+[5,6,7]
l = l-[3,5]
l.each{println it}

l = [1,2,3] as Set
m = [course:'gradle', rating:5]
```

<h1>Understand build </h1>  
There are two main components of build.gradle 1, Project and 2, tasks

# Project

all these dependenciesm, repositories etc are parts/methods of of Project object created by Gradle
<br/>
Plugins are just block of code.

ext is used to create custom property.

# Task

```groovy
task deployToStage{
    doLast(){
        println "deploy to Stage"
    }
}

task deployToProd {
    doLast(){
        println "deploy to production"
    }
}

deployToProd.dependsOn deployToStage
deployToProd.finalizedBy cleanupTask

defaultTask "task1, task3"
```

# Build child project

```
gradle :web:build
gradle :web:clean :web:build
```

# Defining depends on in parent level

```groovy
Project(':web'){
    dependecies{
        implementation project(':services')
    }
}
```

# Finding dependencies.

gradle web:dependecies
