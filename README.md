# DO180-apps
DO180 Repository for Sample Applications

## jonwalk-s2i
oc new-project jonwalk-s2i
oc new-app php:7.3 --name=php-helloworld https://github.com/j0hnniewa1ker/DO180-apps#s2i --context-dir php-helloworld
oc logs --all-containers -f php-helloworld-1-build
oc describe deployment/php-helloworld
oc expose service php-helloworld --name jonwalk-helloworld
curl $(oc get route -o jsonpath='{..spec.host}{"\n"}')
