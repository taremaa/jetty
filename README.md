# hipsnip-jetty

A cookbook to setup a Jetty server.

## Requirements

Built to run on Linux distribution. Tested on Ubuntu 12.04.
Depends on the `java` cookbook.

## Usage

By default the Jetty server is running on port 8080, override `node[:jetty][:port]` if you're not happy with that.
As you can see below you can personnalized your Jetty installation thanks to a bunch of attributes to run a Jetty server as you wish.

__N.B:__ Do not freak out when you see this message on the root page of the Jetty server.
```
Error 404 - Not Found.

No context on this server matched or handled this request.
Contexts known to this server are:
```
Everything is alright, it only means that nothing is deployed on the root context which is okay that's your job ;).

## Attributes

```
["jetty"]["user"] = "jetty"
["jetty"]["group"] = "jetty"
["jetty"]["home"] = "/usr/share/jetty"
["jetty"]["port"] = 8080
["jetty"]["args"] = "jetty.port=#{node.jetty.port}" # The default arguments to pass to jetty.
["jetty"]["logs"] = "" # The jetty default folder is $JETTY_HOME/logs/
["jetty"]["java_options"] = "" # Extra options to pass to the JVM

["jetty"]["contexts"] = "#{node.jetty.home}/contexts"
["jetty"]["webapps"] = "#{node.jetty.home}/webapps"

["jetty"]["version"]	= "9.0.2.v20130417"
["jetty"]["link"] = "http://eclipse.org/downloads/download.php?file=/jetty/stable-9/dist/jetty-distribution-9.0.2.v20130417.tar.gz&r=1"
["jetty"]["checksum"] = "6ab0c0ba4ff98bfc7399a82a96a047fcd2161ae46622e36a3552ecf10b9cddb9" # SHA256

["jetty"]["directory"] = "/usr/local/src"
["jetty"]["download"]  = "#{jetty.directory}/jetty-distribution-#{jetty.version}.tar.gz"
["jetty"]["extracted"] = "#{jetty.directory}/jetty-distribution-#{jetty.version}"

["jetty"]["log"]["level"]  = "INFO" # SEVERE ERROR (highest value) WARNING INFO CONFIG FINE FINER FINEST (lowest value)
["jetty"]["log"]["class"] = "org.eclipse.jetty.util.log.StdErrLog"
```

## Cookbook development

You will need to do a couple of things to be up to speed to hack on this cookbook.
Everything is explained [here](https://github.com/hipsnip-cookbooks/cookbook-development) have a look.

## Test

```
bundle exec rake cookbook:full_test
```

## Licence

Author: Rémy Loubradou

Copyright 2013 HipSnip Limited

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.