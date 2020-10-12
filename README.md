# Demo using live coding

### Structure

* **karaf.zip** -- Contains the Karaf container with the bnd agent deployed.
* **org.test** -- The Maven project

### Instructions

* Java 1.8 required
* Import Maven project `org.test` into Eclipse
* Unzip `karaf.zip`
* Run `karaf/bin/karaf`
* Create a distro file for karaf `java -jar bnd.jar remote distro karaf` (make sure file `distro.jar` produced is in the root of this project)
* Run `package bnd-run:run@app` on `org.test` reactor
* Run `list` command in the Karaf shell to see installed bundles and version
* Touch `org.test.bundle`, nothing happen.
* Run `list -u` to see update location of bundles.