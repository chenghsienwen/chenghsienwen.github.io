### Ad domain: dsp
![dsp ecosystem](mdoc-docs/resources/dsp_ecosystem.jpeg)


### Ad domain: ad network
![dsp ecosystem](mdoc-docs/resources/ad_network.jpeg)


### Ad domain: programmatic buying
![programmatic buying](mdoc-docs/resources/programmatic_ad.jpeg)



### vpon dsp architecture
![vpon dsp architecture](mdoc-docs/resources/vpon_dsp_architecture1.jpeg)


### vpon dsp architecture: reporting
![vpon dsp architecture](mdoc-docs/resources/vpon_dsp_architecture_reporting.jpeg)



### Cases study in vpon


### Work done items(2019 April ~ 2023 May)
```
a. system design
  1. cpx& upx feature
  2. viooh screen targeting development on backend
  3. viooh hour of play feature development
  4. Static ad feature development on dsp side
  5. dsp segment ETL for adn segments(adn segment in mysql => kafka connect to consume service => validate and produce to aerospike)
  6. Audience profile service development
b. legacy refinements
  1. Adn x adNext to one console
  2. dsp bidder cold start issue feature (consuling)
  3. Line/camapign budeget control add revenue tracking 
  5. cpx refactor
  5. geo pipeline refinements
  6. segment micro service refactor
  7. frameworks, libs upgrade
  8. bidding rate refinement by adding system wonbid
  9. ssp-info-downloader 
  10. porting dsp agent to DE
  11. prebid, postbid => support ops
c. issue fix
  1. oom issue
  2. ad bidding always not match
  3. static ad can get mock ad
  4. clarify report value not in consistency
  5. over run due to bid rate
  6. service discovery issue: service dis connect and re connect failed due to dependency service redeploy
  7. kafka connect issue: unknown field cause crash
d. tools and dev flow refinements
  1. deploy integration
  1. Finatra template maintain
  2. ad-test-tracker-service(for UAT continence) 
  3. Report-streamer feature test refine spark testing time 
```



### cpx & upx feature
- use case
- functional features
- non functional features
- high level design
- detail level design
    - streamming service flow
    - data model


### Use case
- purpose: conversion tracking
    - conversion pixel(cpx)
    - universal pixel(upx)
- advertiser web site put some event code: 
    - ex: put purchase event in purchase button
- phone app show ad, user click ad and redirect to advertiser web site(ex: Casio)
- user may trigger some events and send to ad platform
- Ad platform would collect conversion of the ad campaign and make analysis report


### functional feature 
- should collect events or conversions
- upx need dashboard to show report
- conversion rules can be modified
- refactor cpx legacy flow for integration


### put event code on landing page
![upx-events-code](mdoc-docs/resources/upx_event_gen1.jpeg)


### dashboard: event activities
![upx-events](mdoc-docs/resources/upx_event1.jpeg)


### dashboard: conversions
![upx-conversions](mdoc-docs/resources/upx_conversion1.jpeg)


### non functional feature
- cpx and upx have to be co-exists
- avalibility: upx event can be unlimited
- scalability: can be scale out and in
- resilient(partial failure)
- fail over in streamming
- security


### high level design
![upx-high-level](mdoc-docs/resources/universal_pixel_v9-universal_pixel.drawio.png)
<!-- .element: style="width:85%;"  -->


### high level design zoom in
![upx-high-level-zoom-in](mdoc-docs/resources/universal_pixel_v9-universal_pixel-streamming-part.drawio.png)
<!-- .element: style="width:85%;"  -->


### streamming services flow
![upx-streamming](mdoc-docs/resources/universal_pixel_v9-validator_aggregator_transfomer.drawio.png)
<!-- .element: style="width:100%;"  -->


### data model
- legacy data model need to be deprecated due to new flow integration
- data model compatible with cpx and upx


### some decision making
- refactor legacy flow or not
- spark-stream vs kafka-stream vs akka-stream
- streaming fail over



### Continuous deployment refinement
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



### test flow refinements
- ad-test-tracker for PM use
- k6 for performance, stress test
- csv to json, protobuf convert
-  optimize test time in CI flow 



### critical project refinement
- legacy code
    - developd from 2x RDs to 5 backend RDs
    - 4x projects in micro service
- project: dsp-agent-bidder
    - start from 2014
    - many tech debts
    - feature test takes 30 mins in jenkins
    - dependencies libs is old and not maintained


### critical project refinement
- refactor in small scale gradually
- seperate some components to other services
- upgrade libs, build tool and scala version
    - scala2.11 to scala2.12
    - spray framework to akka-http
    - fix memory issue
- performance test by [k6](https://k6.io/) rather than JMeter<!-- .element: target="_blank" -->