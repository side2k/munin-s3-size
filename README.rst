========================
S3 bucket size plugin for Munin
========================
:Language: Python
:Author: side2k

Description
==============
Munin plugin for monitoring Amazon S3 storage usage per bucket
Plugin uses s3cmd command to list buckets.

Installation
==============

As root(or using sudo):	
::
	cd /etc/munin/plugins
	ln -s /path/to/s3_bucket_plugin

Configuration
==============

Normally, the only thing you have to config is the user, under which the plugin should be run.
Put this in your /etc/munin/plugin-conf.d/munin-node (or whatever) file:
::
	[s3_bucket_size]
	user <your_username>

***your_username*** should have .s3cfg file in his home directory. You can generate this file by running command below:
::
	s3cmd --configure

Of course, this command shoud be run under the same user, the plugin will run under.