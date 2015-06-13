# Mule Webapp Sample on Openshift

This example demonstrates how to wrap a Mule application as a JavaEE web-application (WAR).

It exists to address the following common issues:

- Using HTTP instead of Servlet inbound endpoints,
  which works but makes no sense because it bypasses the web tier from the web container
  and starts a Mule HTTP server in it.
- Trying to deploy Mule as a Tomcat service,
  which is complex, does not bring tons of benefits as opposed to simply deploying a WAR.


Running the WAR on OpenShift
----------------------------

Register at http://openshift.redhat.com/, and then create a Tomcat 7 application:

    rhc app create -a muleontomcat -t jbossews-2.0 -n appdomainname -l your-openshift-login-name

Add this upstream git repo:

    cd muleontomcat
    git remote add quickstart -m master https://github.com/tyrell/mule-webapp-openshift.git
    git pull -s recursive -X theirs quickstart master
    
Then push the repo upstream:  

    git push

That's it, you can now see your running application at:

    http://muleontomcat-yournamespace.rhcloud.com/app/hello

Updating your application
----------------------------

To deploy your changes to openshift just add your changes to the index, commit and push:

    git add . -A
    git commit -m "a nice message"
    git push

**Copyright © 2015 Tyrell Perera - MIT License**
