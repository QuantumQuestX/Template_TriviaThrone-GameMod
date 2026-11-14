# Example game mod

This project demonstrates a complete, single-question game mod: a `mod.xml` manifest, a Java
`ServiceLoader` entry, a game provider/definition/session, a creator that produces a
`.game.throne` archive, and small editor and gameplay pages.

The template is a standalone Maven project. It depends on Game API `2.0.0-SNAPSHOT`, which is not
yet published. From the TriviaThrone source tree, build and install that API into your local Maven
repository:

```sh
./mvnw -pl triviathrone-api/game-api -am install -DskipTests
```

Then, from this directory, build it with:

```sh
mvn clean verify
```

Copy `target/example-game-mod-1.0.0-SNAPSHOT.jar` to `mods/games/` and restart the server. The game
appears in the game creator; its editor downloads a quiz package, and the custom game page lets the
host reveal the answer. When the server's API is released or upgraded, set `triviathrone.api.version`
in `pom.xml` and the manifest's `apiVersion` to the matching versions. The example uses only the
game API at runtime; bundle any additional runtime dependencies your mod introduces.
