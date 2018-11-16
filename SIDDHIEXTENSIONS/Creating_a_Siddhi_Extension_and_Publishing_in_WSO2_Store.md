# Creating a Siddhi Extension and Publishing in WSO2 Store

-   [Introduction](#CreatingaSiddhiExtensionandPublishinginWSO2Store-Introduction)
-   [Basic implementation
    requirements](#CreatingaSiddhiExtensionandPublishinginWSO2Store-Basicimplementationrequirements)
-   [Images required for
    publishing](#CreatingaSiddhiExtensionandPublishinginWSO2Store-Imagesrequiredforpublishing)
-   [Publishing the
    extension](#CreatingaSiddhiExtensionandPublishinginWSO2Store-Publishingtheextension)

### Introduction

This section provides information on the high-level tasks involved in
implementing and publishing Siddhi extensions in [WSO2
Store](https://store.wso2.com/store).

### Basic implementation requirements

1.  Research the area related for which you want to create an Siddhi
    extension.
2.  Required template can be created using the maven archetype found
    with following and using the mentioned command. 

-   -   <https://github.com/wso2-extensions/archetypes/tree/master/siddhi-window-archetype> to
        create Siddhi window extension use following command.

        mvn archetype:generate
        -DarchetypeGroupId=org.wso2.carbon.extension.archetype
        -DarchetypeArtifactId=org.wso2.extension.siddhi.window-archetype
        -DarchetypeVersion=2.0.0
        -DgroupId=org.wso2.siddi.extension.window
        -DartifactId=org.wso2.siddi.extension.window.sample
        -Dversion=1.0.0
        -DarchetypeRepository=<http://maven.wso2.org/nexus/content/repositories/wso2-public/>

         

    -   <https://github.com/wso2-extensions/archetypes/tree/master/siddhi-aggregator-archetype> to
        create Siddhi aggregate extension use following command.

        mvn [archetype:generate](http://archetypegenerate/) -DarchetypeGroupId=org.wso2.carbon.extension.archetype
        -DarchetypeArtifactId=org.wso2.siddi.extension.cep.aggregator-archetype
        -DarchetypeVersion=2.0.1
        -DgroupId=org.wso2.siddi.extension.aggregation
        -DartifactId=org.wso2.siddi.extension.aggregation.sample
        -Dversion=1.0.0
        -DarchetypeRepository=<http://maven.wso2.org/nexus/content/repositories/wso2-public/>

         

    -   <https://github.com/wso2-extensions/archetypes/tree/master/siddhi-function-archetype> to
        create Siddhi function extension use following command.

        mvn [archetype:generate](http://archetypegenerate)
        -DarchetypeGroupId=org.wso2.carbon.extension.archetype
        -DarchetypeArtifactId=org.wso2.siddi.extension.cep.function-archetype
        -DarchetypeVersion=2.0.1
        -DgroupId=org.wso2.siddi.extension.function
        -DartifactId=org.wso2.siddi.extension.function.sample
        -Dversion=1.0.0
        -DarchetypeRepository=<http://maven.wso2.org/nexus/content/repositories/wso2-public/>

         

    -   <https://github.com/wso2-extensions/archetypes/tree/master/siddhi-stream-processor-archetype> to
        create Siddhi stream processor extension use following command.

        mvn [archetype:generate](http://archetypegenerate)
        -DarchetypeGroupId=org.wso2.carbon.extension.archetype
        -DarchetypeArtifactId=org.wso2.siddi.extension.cep.streamProcessor-archetype
        -DarchetypeVersion=2.0.1
        -DgroupId=org.wso2.siddi.extension.streamprocessor
        -DartifactId=org.wso2.siddi.extension.streamprocessor.sample
        -Dversion=1.0.0
        -DarchetypeRepository=<http://maven.wso2.org/nexus/content/repositories/wso2-public/>

         

    -   <https://github.com/wso2-extensions/archetypes/tree/master/siddhi-stream-function-archetype> to
        create Siddhi stream function extension use following command.

        mvn
        [archetype:generate](http://archetypegenerate) -DarchetypeGroupId=org.wso2.carbon.extension.archetype
        -DarchetypeArtifactId=org.wso2.siddi.extension.cep.streamFunction-archetype
        -DarchetypeVersion=2.0.1
        -DgroupId=org.wso2.siddi.extension.streamfunction -DartifactId=org.wso2.siddi.extension.streamfunction.sample
        -Dversion=1.0.0 -DarchetypeRepository=<http://maven.wso2.org/nexus/content/repositories/wso2-public/>

         

The following sections explain how we can create different types of
Siddhi Extensions in details,

-   [Writing a Custom Aggregate
    Function](https://docs.wso2.com/display/CEP410/Writing+a+Custom+Aggregate+Function)
-   [Writing a Custom Window
    Extension](https://docs.wso2.com/display/CEP410/Writing+a+Custom+Window+Extension)
-   [Writing a Custom Function
    Extension](https://docs.wso2.com/display/CEP410/Writing+a+Custom+Function+Extension)
-   [Writing a Custom Stream Function
    Extension](https://docs.wso2.com/display/CEP410/Writing+a+Custom+Stream+Function+Extension)
-   [Writing a Custom Stream Processor
    Extension](https://docs.wso2.com/display/CEP410/Writing+a+Custom+Stream+Processor+Extension)

 

We strongly recommend the non-use of GPL or LGPL licensed libraries in
the development of extensions. If there is a reason to use these
licenses, the reason needs to be provided along with the extension
submission. Hosting extensions that use GPL or LGPL licenses in WSO2
Store will be done at the sole discretion of WSO2 and provision of a
reason for the use of GPL LGPL licensed libraries does not guarantee
hosting such extension.

### Images required for publishing

You need to have PNG images with the following dimensions so that those
can be used in the WSO2 store.

-   580x300
-   220x200

### **Publishing the extension**

When the extension development is complete, create
a [JIRA](https://wso2.org/jira/projects/ANLYEXT/) under the **Siddhi
Extensions** project with the following information:

-   Source code can be directly attached to the JIRA or do the
    development in your own git repo.
-   Once we review the code we will create a repo under 
    **<https://github.com/wso2-extensions>, **and ask you to send the
    pull request.
-   If GPL or LGPL licensed connectors are used, specify reasons for the
    use of such libraries. 

 

1218

137

2248

2461

2467

286
