# devonfw guide

---

**IMPORTANT**

Download the **continuously updated devonfw guide** from [here](https://github.com/devonfw/devonfw-guide/raw/master/devonfw_guide.pdf).

---

This repository contains a collection of guides and documents from the different devonfw's modules, such as:

- **cicdgen**: Tool to generate CI/CD configurations for devonfw projects.
- **devon4j**: Module for Java
- **devon4net**: Module for .net
- **devon4ng**: Module for Angular
- **devonfw shop floor**: Set of documentation, tools and methodologies used to configure provisioning, development and uat environments used in devonfw projects.
- **devonfw testing**: Module for testing.
- **My Thai Star**: devonfw reference application.
- **CobiGen**: Code-based incremental generator.

## How is this guide organized

Each submodule contains a master file _name-of-the-wiki.wiki/master-name-of-the-wiki.asciidoc_ which includes all the other files in the submodule. All master-*.asciidoc files are joined in *devonfw-guide/master.asciidoc\*, this way, all documents are linked and can be used to generate a unique file.

## How to generate a PDF

Please find the documentation how to generate a PDF for your project / wiki in the [devon-docgen repository](https://github.com/devonfw/devon-docgen).

**IMPORTANT**

If your directory contains huge amounts of files, maven can throw a OutOfMemoryError. More info at [Maven OutOfMemoryError](https://cwiki.apache.org/confluence/display/MAVEN/OutOfMemoryError)

---
