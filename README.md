# NappMusic Project and Dependencies

[NappMusic] is a university project application for reproducing music
found in your computer or online.

This is not a polished product,
but we leave the instructions necessary to run it for anyone interested,
including our future selves.

[NappMusic]: /NappMusic

## Installation of Dependencies and Compilation

NappMusic dependencies are handled using [Maven].
To compile NappMusic:

* Init the git submodules with `git submodule update --init --recursive`.
Otherwise, they will be empty folders.

* Install two external components in your Maven repository.
They are also referenced in this repository as git submodules.
[UiButton] and [SongLoader].
You can do it executing `mvn install` inside those directories.

* Install a Jar file that contains a driver to use the database.
(Unfortunately, it was provided by our professors as is.
Therefore, we can't include it as source code.)
From the NappMusic directory type:

```sh
mvn install:install-file -Dfile=H2/DriverPersistencia.jar -DgroupId=um.tds -DartifactId=DriverPersistencia -Dversion=1.0 -Dpackaging=jar -DgeneratePom=true
```

* Create a jar file of NappMusic with `mvn compile`.

[Maven]: https://maven.apache.org/
[UiButton]: /UiButton
[SongLoader]: /SongLoader

## Running the application

* You need to run the database under [H2] before trying to run the application.

```sh
jva -jar H2/ServidorPersistencia.jar
```

* After you compile NappMusic with `mvn compile package`,
you can run it `mvn exec:java -Dexec.mainClass=um.tds.nappmusic.gui.LoginWindow`.
