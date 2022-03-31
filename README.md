# toolisticon-maven-tiles

Reusable, modular [maven-tiles](https://github.com/repaint-io/maven-tiles) for holistic OSS projects.


![warning](https://img.shields.io/badge/WARNING-internal%20use%20only-red)
[![Build Status](https://github.com/toolisticon/maven-tiles/workflows/Development%20branches/badge.svg)](https://github.com/toolisticon/maven-tiles/actions)
[![sponsored](https://img.shields.io/badge/sponsoredBy-Holisticon-RED.svg)](https://holisticon.de/)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/io.toolisticon.maven/maven-tiles/badge.svg)](https://maven-badges.herokuapp.com/maven-central/io.toolisticon.maven/maven-tiles)

## Important note

This is a collection of tiles we re-use for our own OSS projects. It is [not encouraged](https://github.com/repaint-io/maven-tiles#final-notes) to just use these tiles yourselves:

> Tiles-Maven works best when you and your team own the tiles. I don’t recommend relying on open source tiles, always create your own versions and always lock down versions of third party tiles, just like you would third party dependencies.

That being said ... let's have some fun with tiles.

## kotlin-compile-tile

Defined in [kotlin-compile-tile/tile.xml](/kotlin-compile-tile/tile.xml)

**Usage**

```xml
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <kotlin.version>1.6.10</kotlin.version>
    <java.version>17</java.version>
  </properties>

  <build>
    <plugins>
      <plugin>
        <groupId>io.repaint.maven</groupId>
        <artifactId>tiles-maven-plugin</artifactId>
        <extensions>true</extensions>
        <configuration>
          <filtering>true</filtering>
          <tiles>
            <tile>io.toolisticon.maven.tile:kotlin-compile-tile:${project.parent.version}</tile>
          </tiles>
        </configuration>
      </plugin>
    </plugins>
  </build>
```

**required properties**

* `${kotlin.version}`
* `${java.version}`
* `${project.build.sourceEncoding}` 

**Features**

* provides dependencies to
  * `kotlin-stdlib-jdk8`
  * `kotlin-reflect`
* Provides plugins 
  * `kotlin-maven-plugin` - includeing allopen and noarg dependencies
  * `maven-compiler-plugin` - disabling default java compile
  * `build-helper-maven-plugin` to include kotlin sources in deployment
  * `dokka-maven-plugin` for kdoc documentation 
  * `maven-javadoc-plugin`
