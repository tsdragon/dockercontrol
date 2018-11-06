# dockercontrol

This is just a simple set of scripts to help me update/manage/rebuild the docker images on my server

simple usage is just copy them somewhere, create some scripts to build the containers (included a hello-workd container as an example) then run either rebuild_all or rebuild_container

# rebuild_all

rebuild_all is used when you want to rebuild all, or at least a bunch of containers all at once.  you can tell it to nuke everything, carefully rebuild all the images one by one, or just specify a few you'd like to rebuild.

It will also restart the containers once they're rebuilt automatically, inless you specify not to reboot any containers.  You can also pass in individual container names to skip rebooting.

Usage: rebuild_all [option...] -c containername -c containername... -e containername -e containername... 

&nbsp;&nbsp;-n,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Nuke, completely wipe ALL containers (USE EXTREME CAUTION)<br>
&nbsp;&nbsp;-d,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Don't restart the containers<br>
&nbsp;&nbsp;-c name,&nbsp;&nbsp;Manually give list of containers to rebuild instead of rebuilding all of them<br>
&nbsp;&nbsp;-e name,&nbsp;&nbsp;Don't restart this container like the others<br>


# rebuild_container

rebuild_container is used by rebuild_all but can be used on its own to rebuild contianers.  Just create a build script (The filename must be the same as the container name!) then run rebuild_container.

You can specify options to stop, remove, and rmi the container and image before it's rebuilt if needed.

Usage: rebuild_container [option...] -n containername

&nbsp;&nbsp;-n name,&nbsp;&nbsp;Specify container name (required)<br>
&nbsp;&nbsp;-x,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Stop the container<br>
&nbsp;&nbsp;-r,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Remove the container<br>
&nbsp;&nbsp;-i,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Remove the container image<br>
&nbsp;&nbsp;-s,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Restart the container after execution<br>
