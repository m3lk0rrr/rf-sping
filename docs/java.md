

#### 1. ensure correct java 17 (latest _highly_ supported lts version as of early 2026)

```bash
sudo apt-get install openjdk-17-jdk -y
sudo apt-get install maven -y


# check for any other environment or .bashrc or .profile configured jdk installations!

sudo update-alternatives --config java
sudo update-alternatives --config javac
# selected 17, from openjdk


$ java --version
# openjdk 17.0.17 2025-10-21
# OpenJDK Runtime Environment (build 17.0.17+10-Ubuntu-124.04)
# OpenJDK 64-Bit Server VM (build 17.0.17+10-Ubuntu-124.04, mixed mode, sharing)

$ javac --version
javac 17.0.17

```


#### 2. try to find intellij idea _community_ edition, if you _can_ =))))

Other versions...

https://www.jetbrains.com/idea/download/other.html


##### unpack it somewhere like

/home/hello/App/ideaIC/idea-IC-252.28539.33

./bin/idea

- skip import from vs
- install SonarCube plugin from SonarSource
- restart

#### 3. create new spring project. 

on https://start.spring.io/

- maven
- java 
- 3.5.9 latest lts like version
- java 17 config
- jar packaging
- properties configuration

add:
- spring boot devtools
- spring configuratio processor
- spring web
- spring data jpa
- postgresql driver
- spring boot actuator
- lombok

##### generate, download, extract, ???, profit


#### 4. cleaup the download demo thingy

- /home/hello/DEV/JAVA/rf-demo

```bash
# we are using the system installed maven, not the included portable one

# cleaup
$ # rm mvnw mvnw.cmd .mvn/ -rf

# no DB currently, even for tests:
echo "spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration" | tee -a "src/main/resources/application.properties"

# try to build it
mvn clean install -U
```


#### 5. add git(hub)

```bash
# initalize empty repository
git init .

# check files for no clutter (edit .gitignore if needed)
git status

# no credentials or sensitive things in the codebase currently, right? =)
git add .
git commit -m "initial commit"


# create new repo in github, added ssh keys

# check for any credentials or sensitive informations
# - no keys, the names are mostly scrubed (rf as namespace)

# register remote locally
git remote add origin git@github.com:m3lk0rrr/rf-sping.git
# fetch remote for merging already existing licence and remote history
git fetch origin
# merge the remote local branches
git merge origin/main --allow-unrelated-histories
# rename the local branch (it was created as 'master')
git branch -M main


# try to build it again
mvn clean install

# push it to github
git push -u origin main
```


#### 6. open it ideaC

##### change maven settings:
Build, Execution, Delpoyment > Build Tools > Maven

```bash
mvn --version | grep home
# Maven home: /usr/share/maven
```

Specify '/usr/share/maven' as 'Maven home path'.
Exact version will shown if everything okay.


##### import/open project as "Maven project"


##### Right click on the imported project, like 'rf-demo'.


Project Settings > SDK

Select the 17 jdk, and the language level as 17.
We will configure later with the maven pom.xml also.

Let it go^TM indexing. Pray for the Gods (Dijkstra, Neumann), also show a 'Sacrifice': grab a cup of coffee or tea.

##### do the 'Maven dance'
Sync all the maven projects on the Maven tab, recycle icon.

Build menu > Rebuild project
Build Menu > Build project
Build menu > Rebuild project

##### Try to run the DemoApplication, and the DemoApplicationTests within the editor with the green runners on the sidebar
