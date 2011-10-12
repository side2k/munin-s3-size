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

**your_username** should have .s3cfg file in his home directory. You can generate this file by running command below:
::
	s3cmd --configure

Of course, this command shoud be run under the same user, the plugin will run under.

Also, you can configure **s3_cache_expiry** option, which points, in seconds, how frequently your S3 buckets will actually be requested. By default it is set to 3600, which means that buckets will be listed once in an hour. This value can't be smaller than munin update interval.

Example config
==============

Here's the sample config:

::
	[s3_bucket_size]
	user jack
	env.s3_cache_expires 600 
	
With this config plugin will update your bucket sizes every	10 minutes, and plugin will run under user jack.