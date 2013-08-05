manas-mvn
=========

manas deployed



Maven Remote Repository for Manas Artifacts

How to use this repository
--------------------------

###Add the following to your ```pom.xml``` of the project you need to access the repo from:

```
<repositories>
    <repository>
        <id>xef-snapshots</id>
        <url>https://raw.github.com/lanceriedel/manas-mvn/master/snapshots</url>
        <snapshots>
     		<enabled>true</enabled>
      		<updatePolicy>always</updatePolicy>
   		</snapshots>
    </repository>
    <repository>
        <id>xef-releases</id>
        <url>https://raw.github.com/lanceriedel/manas-mvn/master/releases</url>
    </repository>
</repositories>
```

To deploy to this repository
----------------------------
###Clone the git repository locally:
```$> git clone https://github.com/lanceriedel/manas-mvn.git```

###Add the following to the ```pom.xml``` of the artifact to be deployed:
```
<properties>
  <!--maven variable which points to your local repository -->
  <internal.repo.path>file:///home/mr/tmp/manas-mvn/</internal.repo.path>
</properties>

 <distributionManagement>
 	<repository>
    	<id>internal.repo</id>
    	<name>Internal Repository</name>
    	<url>${internal.repo.path}</url>
	</repository>   
</distributionManagement>
```

###With this set, you can deploy our project:
```mvn deploy```

###Push Repo
After this is complete, switch to your remote maven repository git project, and execute:

```
git add .
git commit -m "Hopefully descriptive release notes!"
git push origin master
```
