# Karaf Camel Log QuickStart

This quickstart shows a simple Apache Camel application that logs a message to the server log every 5th second.
It also shows how Karaf assembly files can be overridden using resources from `src/main/resources/assembly/`. The included sample log file `etc/org.ops4j.pax.logging.cfg` sets the log level to DEBUG. 

This quickstart will automatically create a ConfigMap named karaf-camel-log and will set up service account view policy.
By default the view policy will be applied to a service account named `default` in namespace `default`, you can customize them via quickstart.namespace and quickstart.serviceaccount properties.

### Building

The example can be built with

    mvn clean install -Ddocker.skip


### Running the example in fabric8

It is assumed that OpenShift platform is already running. If not you can find details how to [Install OpenShift at your site](https://docs.openshift.com/enterprise/3.1/install_config/install/index.html).

The example can be built and deployed using:

    mvn install fabric8:deploy

When the example runs in OpenShift, you can use the OpenShift client tool to inspect the status

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the OpenShift [web console](https://docs.openshift.com/enterprise/3.1/getting_started/developers/developers_console.html#tutorial-video) to manage the
running pods, and view logs and much more.


### Running the example using OpenShift S2I template

The example can also be built and run using the included S2I template quickstart-template.json.

The application can be run directly by first editing the template file and populating S2I build parameters, including the required parameter GIT_REPO and then executing the command:

    oc new-app -f quickstart-template.json

Alternatively the template file can be used to create an OpenShift application template by executing the command:

    oc create -f quickstart-template.json


### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.

