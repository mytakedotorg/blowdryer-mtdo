
# MyTake.org [Blowdryer](https://github.com/diffplug/blowdryer) scripts

[![License Apache 2.0](https://img.shields.io/badge/license-apache--2.0-brightgreen.svg)](https://tldrlegal.com/license/apache-license-2.0-(apache-2.0))
[![Changelog](https://img.shields.io/badge/keepachangelog-yes-brightgreen.svg)](#changelog)

## Users

| user                                                                     | updated on  | to version |
| :----------------------------------------------------------------------- | :---------- | :--------- |
| [mtdo:factset-tooling](https://github.com/mytakedotorg/mtdo/tree/staging/factset-tooling) | 2020-09-25  | `1.0.0`    |

## Available scripts (without `.gradle` extension)

- **spotless/freshmark** - applies to `*.gradle` and `*.md`
  - if `com.diffplug.spotless-changelog` is applied in this or the parent project, then `versionLast` will be set in freshmark
- **spotless/java** - applies to `*.gradle` and java sourcesets
  - `干.proj('license', 'supported: [apache, agpl]')`
- **base/java8** - sets up java 8 with UTF-8, clean eclipse projects, and mavenCentral
- **base/changelog** - pulls version information from a changelog in either the same project or the parent project
- **base/gradle-plugin** - sets up gradle plugin metadata and plugin portal publishing, fixes eclipse to hook gradle
  - requires `id 'com.gradle.plugin-publish' version '0.10.1'`
  - `干.proj('git_url', 'the git url with no protocol, e.g.: github.com/mytakedotorg/mtdo')`
  - `干.proj('plugin_tags', 'space-delimited list of tags for the gradle plugin portal')`
  - `干.proj('plugin_list', 'space-delimited list of plugin names')`
    - `干.proj("plugin_${plugin}_id", "for ${plugin}: apply plugin: 'id'")`
    - `干.proj("plugin_${plugin}_impl", "for ${plugin}: implementationClass")`
    - `干.proj("plugin_${plugin}_name", "for ${plugin}: name for the plugin portal")`
    - `干.proj("plugin_${plugin}_desc", "for ${plugin}: description for the plugin portal")`
    - optional: `"plugin_${plugin}_tags" : space-delimited list of tags to override plugin_tags only for ${plugin}`
- **base/maven** - sets up maven-publish and javadoc
  - `干.proj('git_url', 'the git url with no protocol, e.g.: github.com/mytakedotorg/mtdo')`
  - `干.proj('maven_group', 'the maven group, recommend org.mytake')`
  - `干.proj('maven_artifact', 'the maven artifactId')`
  - `干.proj('maven_name', 'human-friendly name')`
  - `干.proj('maven_desc', 'human-friendly description')`
  - `干.proj('javadoc_links', "space-delimited links, if you add '/package-list' to the urls you should get a package list")`
  - `干.proj('license', 'supported: [apache, agpl]')`

# Changelog

## [Unreleased]
### Added
* Add `toggleOffOn()` to all the spotless formatters.

## [1.0.0] - 2020-09-19
### Changed
* First release

<!-- END CHANGELOG -->

# Acknowledgements

- Forked from [blowdryer-diffplug](https://github.com/diffplug/blowdryer-diffplug) on September 18, 2020
- Thanks to [Lars Grefer](https://github.com/larsgrefer) and [Dennis Fricke](https://github.com/Frisch12) for
  - [`JavadocUtf8Plugin`](https://github.com/freefair/gradle-plugins/blob/6d6f5ff6036e7da1c329075a02c6452c0bb669be/maven-plugin/src/main/java/io/freefair/gradle/plugins/maven/javadoc/JavadocUtf8Plugin.java), licensed under the [MIT License](https://github.com/freefair/gradle-plugins/blob/6d6f5ff6036e7da1c329075a02c6452c0bb669be/LICENSE), used [here](https://github.com/mytakedotorg/blowdryer-mtdo/blob/9fcb5e22b9ba2cc1c0884c4fb60b4080687b2435/src/main/resources/base/javadoc-agg.gradle#L38-L41).
  - [`JavadocJarPlugin`](https://github.com/freefair/gradle-plugins/blob/6d6f5ff6036e7da1c329075a02c6452c0bb669be/maven-plugin/src/main/java/io/freefair/gradle/plugins/maven/javadoc/JavadocJarPlugin.java), licensed under the [MIT License](https://github.com/freefair/gradle-plugins/blob/6d6f5ff6036e7da1c329075a02c6452c0bb669be/LICENSE), used [here](https://github.com/mytakedotorg/blowdryer-mtdo/blob/9fcb5e22b9ba2cc1c0884c4fb60b4080687b2435/src/main/resources/base/javadoc-agg.gradle#L52-L60).
