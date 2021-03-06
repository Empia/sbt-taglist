# About

Small SBT plugin that will contain roughly the functionality of the maven-tag-list plugin when done.


The plugin contains the task "tag-list" which performs a case insensitive search in the sources 
of a project for a set of keywords. The default keywords are "todo" and "fixme"

# Installation

Add the following lines to ~/.sbt/plugins/build.sbt or PROJECT_DIR/project/plugins.sbt:

    resolvers += "sbt-taglist-releases" at "http://johanandren.github.com/releases/"

    addSbtPlugin("com.markatta" % "taglist-plugin" % "1.3")


And then this line to PROJECT_DIR/build.sbt to include the task tag-list into your project:


```
import com.markatta.sbttaglist.TagListPlugin

TagListPlugin.tagListSettings
```

# Configuration
The plugin uses the regular source settings for your sbt-project so it should work out of the box with non-standard directory structures etc. 

###1.3:
The default tags looked for are "todo" and "fixme". To override those you can either just simply set a list of words,
all of them will yield warnings in the log when found:

```
import com.markatta.sbttaglist.TagListPlugin

TagListPlugin.TagListKeys.tagWords := Seq("incorrect", "plainwrong", "dontcheckin")
```

Or if it better suits your needs you can specify each word along with a log level:

    TagListPlugin.TagListKeys.tags := Seq(Tag("todo", TagListPlugin.Info), Tag("fixme", TagListPlugin.Info))

