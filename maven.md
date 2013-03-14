Maven
-----

### Create & Import a new Project

    cd /tmp
    mkdir project1
    cd project1/
    mkdir tags branches
    mvn archetype:create -DarchetypeGroupId=org.apache.maven.archetypes -DgroupId=uk.co.arunhorne -DartifactId=project1
    mv project1 trunk
    cd trunk

Now edit pom.xml, remove dummy tests created by the archetype etc.

    cd /tmp
    svn import -m "Skeleton for project1" project1 https://svn.arunhorne.co.uk/svn/project1
