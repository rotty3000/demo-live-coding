# Demo using live coding

### Structure

* **karaf.zip** -- Contains the Karaf container with the bnd agent deployed.
* **org.test** -- The Maven project

### Instructions

* Java 1.8 (min) required

* (optional) Import Maven project `org.test` into IDE setup for live coding (Eclipse + Bndtools is a good option), or just use cli

* Unzip `karaf.zip` to `karaf/`

* Get the **bnd remote agent**

  * `mvn dependency:get -Dartifact=biz.aQute.bnd:biz.aQute.remote.agent:5.1.2`

* Place the remote agent jar (`~/.m2/repository/biz/aQute/bnd/biz.aQute.remote.agent/5.1.2/biz.aQute.remote.agent-5.1.2.jar`) in the `karaf/deploy` dir

* In one terminal (terminal A), execute `karaf/bin/karaf`

* Get the **bnd cli**

  * `mvn dependency:get -Dartifact=biz.aQute.bnd:biz.aQute.bnd:5.1.2`

* In another terminal (terminal B), create a **distro** file for Karaf

  * ```bash
    bnd_jar=~/.m2/repository/biz/aQute/bnd/biz.aQute.bnd/5.1.2/biz.aQute.bnd-5.1.2.jar
    java -jar $bnd_jar remote distro karaf
    ```

  * make sure the resulting `distro.jar` file is placed in the root of this project, that is where the build expects it

* In terminal B, move into the `org.test` directory

* In terminal B, execute `mvn package bnd-run:run@app`

* In terminal A, run `list` command in the Karaf shell to see installed bundles and version

* In another terminal or in the IDE make any change that would cause the modules of `org.test` to be rebuilt

* In terminal A, run `list -u` to see updated bundles