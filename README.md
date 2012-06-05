GateIn portal on OpenShift Express
============================================
Installing the GateIn project on OpenShift was never easier!

This git repository helps you get up and running quickly with the GateIn project.

Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a jbossas-7.0 application

    rhc app create -a portal -t jbossas-7.0

Add this upstream openshift-portal repo

    cd portal
    git remote add upstream -m master git://github.com/eschabell/openshift-portal.git
    git pull -s recursive -X theirs upstream master
    # note that the git pull above can be used later to pull updates.
    
Issue the following command to determine your USERID
 
    less .git/config | grep url
 
This will display something like:
 
    url = ssh://USERID@portal-$yourdomain.rhcloud.com/~/git/portal.git/
 
Where USERID is a hash string.

Open .openshift/config/standalone.xml for editing, and replace the two occurrences of ${USER_ID} with your actual value.
Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://portal-$your_domain.rhcloud.com/portal

