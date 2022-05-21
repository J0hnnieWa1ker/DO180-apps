# DO180-apps
DO180 Repository for Sample Applications

## jonwalk-s2i
oc new-project jonwalk-s2i
oc new-app php:7.3 --name=php-helloworld https://github.com/j0hnniewa1ker/DO180-apps#s2i --context-dir php-helloworld
oc logs --all-containers -f php-helloworld-1-build
oc describe deployment/php-helloworld
oc expose service php-helloworld --name jonwalk-helloworld
curl $(oc get route -o jsonpath='{..spec.host}{"\n"}')
# edit index.php
oc start-build php-helloworld
oc logs php-helloworld-2-build -f
curl -s $(oc get route -o jsonpath='{..spec.host}{"\n"}')

## temps
oc new-project jonwalk-temps

oc new-app php:7.3~https://github.com/RedHatTraining/DO180-apps --context-dir temps --name temps
oc logs -f bc/temps
oc get pods -w
oc expose svc/temps
oc get route/temps
open http://temps-jonwalk-temps.itzroks-6640022so7-a2j02q-4b4a324f027aea19c5cbc0c3275c4656-0000.us-south.containers.appdomain.cloud
