GateIn portal on OpenShift Express
============================================
Installing the GateIn project on OpenShift was never easier!

This git repository helps you get up and running quickly with the GateIn project.

Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a jbossas-7.0 application

    rhc app create -a portal -t jbossas-7.0 --from-code git://github.com/eschabell/openshift-portal.git
    
Issue the following command to determine your USERID
 
    rhc app show

This will display something like:
 
    (uuid: dee08c9861f54a6b9bfcb968c356b4c4)
 
Where USERID is a hash string.

Open .openshift/config/standalone.xml for editing, and replace the two occurrences of ${USER_ID} with your actual value.

Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://portal-$your_domain.rhcloud.com/portal

