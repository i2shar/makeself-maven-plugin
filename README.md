Makeself Maven Plugin
=====================

[![Build Status](https://travis-ci.org/hazendaz/makeself-maven-plugin.svg?branch=master)](https://travis-ci.org/hazendaz/makeself-maven-plugin)
[![Maven central](https://maven-badges.herokuapp.com/maven-central/com.github.hazendaz.maven/makeself-maven-plugin/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.hazendaz.maven/makeself-maven-plugin)
[![License](http://img.shields.io/:license-glp-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

![hazendaz](src/site/resources/images/hazendaz-banner.jpg)

Makeself Maven Plugin provides maven integration for megastep makeself script.

Makeself is a self-extracting archiving tool for Unix systems, in 100% shell script.

With help of Cygwin, git for windows or other tools supplying bash for windows, this tool is fully functional with windows.

To use in windows, configure Bash or Add git for windows '/usr/bin' to environment 'Path' variable to execute this plugin.

See [makeself](https://github.com/megastep/makeself)

Example Usage

```xml
            <plugin>
                <groupId>com.github.hazendaz.maven</groupId>
                <artifactId>makeself-maven-plugin</artifactId>
                <version>1.0.0-SNAPSHOT</version>
                <configuration>
                    <archiveDir>distro</archiveDir>
                    <fileName>installDistro.sh</fileName>
                    <label>Distro Self Extraction</label>
                    <startupScript>./runDistroScript.sh</startupScript>
                </configuration>
                <executions>
                    <execution>
                        <id>makeself</id>
                        <goals>
                            <goal>makeself</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
```

*** Special notes: ***

- Use version 1.0.0.beta3 or better for *nix support.  Earlier versions only worked in windows.
- Use version 1.1.4 to avoid dead lock when buffer is overrun.

## Contributor Consideration ##

Executable Permissions on Shell Scripts

When makeself is updated on this repository, perform the following commands after the update commit.  This will ensure shell files are executable within project.
While it might not provide any benefit upon build, it doesn't hurt.

```git
    git add --chmod=+x *.sh; \
    git commit -m "Force makeself to be executable"
```

To check the files are of right permissions

```stat
    stat -c "%a %n" *
```

*** Note: *** It seems no matter the change makself-header.sh wants to stay 644.  Regardless, with all other protections this is handled on *nix now and line endings are addressed.
