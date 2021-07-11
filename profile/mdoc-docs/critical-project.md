### Critical project


### what is critical in R&D team?
![startup-stages](mdoc-docs/resources/startup-stages.jpg)
* ref: https://bcombinator.com/stages-of-a-startup


### what is critical in R&D team?
* in early stage: just want to survive
* in growth stage: pay tech debt
* in expansion stage: how to scale up


### speed and stability are criterial
* how to poc quickly
* how to keep productivity in all members
* how to avoid slow down due to tech debt


### case1: Continuous deployment refinement
#### we use ansible to deploy service
- RD need to 
    - modify /etc/hosts, 
    - pull image at deploy server
    - modify image tag in ansible group variable,
    - run ansible playbook 


#### how to make it easier?
- make a tool to do automation
    - just a command to do all the things
    - can be runed in jenkins on prod
    - can be scalable to all cases by adding config
    - ex:

```shell
./deployIntegration.sh -p [project name] -b [branch] -v 3_0d2201c
```


### case2: project templates
- we have 2 main framework in backend
    - finagle and akka-http
    - so many poc and workaround in micro service
    - CI/CD setting takes time for new members


### case2: project templates
- introduce finagle based framework: finatra
- target: RD don't need to suffer CI/CD setting anymore
- make a clean code architecture
    - impove maintainability and readibility
- add coding convention in template
- productivity for focusing on business features 


### case3: critical project refinement
- legacy code
    - developd from 2x RDs to 5 backend RDs
    - 4x projects in micro service
- project: dsp-agent-bidder
    - start from 2014
    - many tech debts
    - feature test takes 30 mins in jenkins
    - dependencies libs is old and not maintained


### case3: critical project refinement
- refactor in small scale gradually
- seperate some components to other services
- upgrade libs, build tool and scala version
    - scala2.11 to scala2.12
    - spray framework to akka-http
    - fix memory issue
- performance test by [k6](https://k6.io/) rather than JMeter<!-- .element: target="_blank" -->
- add test tool
    - ad-test-tracker for PM use
    - csv to json, protobuf convert