## Chenghsien Wen annual job review 2021
<!-- .element: style="text-align: center"  -->



### About me
![after refinement](mdoc-docs/resources/chenghsienwen_at_vpon.jpeg)
<!-- .element: style="width:100%;"  -->



### annual tasks review
- features
- support colleagues
- development refinements
- research & poc


- features:
    - [Google geo pipeline](http://confluence.vpon.com/display/ADPTM/202101+geo+mapping+refinement)<!-- .element: target="_blank" -->
    - [Adn x adNext phase 2](http://confluence.vpon.com/display/ADPTM/Event+Report)  
    - [Audience profile service development](http://confluence.vpon.com/display/ADPTM/202101+-+Audience+Profile+Service)<!-- .element: target="_blank" -->
    - [Import adn segments to dsp](http://confluence.vpon.com/display/ADPTM/202106+import+adn+segment+to+dsp+for+targeting+POC)<!-- .element: target="_blank" -->
    - [Cpv tracking revenue feature](http://confluence.vpon.com/pages/viewpage.action?pageId=130165738)<!-- .element: target="_blank" -->
    - [H5 creative feature](http://confluence.vpon.com/pages/viewpage.action?pageId=130166576)<!-- .element: target="_blank" -->
    - [Skip off setting in video vast ad](http://confluence.vpon.com/display/ADPTM/202109+skipoffset+on+video+creatives)<!-- .element: target="_blank" -->
    - [app list and domain matching logic](http://confluence.vpon.com/display/ADPTM/202109+app+bundle+and+domain+targeting+poc)<!-- .element: target="_blank" -->
    - [Line/camapign budeget control add revenue tracking](http://confluence.vpon.com/display/ADPTM/202109+Add+ADNW+budget+control+in+DSP)<!-- .element: target="_blank" -->


- support colleagues:
    - Adn audience targetting UAT prepare (support adn team)
    - Support ops for s3 unexpected cost (support ops)
    - [Dsp-reporting new api: site-info](http://confluence.vpon.com/display/ADPTM/202106+Add+publishers+to+Targeting+List+in+manual+optimization)<!-- .element: target="_blank" --> (support frontend RD)
    - Trace bundle criteria issue in bidding flow (pm prod issue)


- development refinements:
    - [Finatra template](https://github.com/chenghsienwen/finatra.g8)<!-- .element: target="_blank" -->  update to 21.1.0 (2021 Oct: 21.9.0)
    - [ad-test-tracker-service](http://ad-test.vpon.com/swagger-docs)<!-- .element: target="_blank" -->(for UAT continence) 
    - [Report-streamer feature test refine spark testing time](http://confluence.vpon.com/display/ADPTM/202104+spark+feature+test+refinement)<!-- .element: target="_blank" -->
    - [Kafka upgrade planing and test, issue fix, monitoring](http://confluence.vpon.com/display/ADPTM/Phase1%3A+kafka+broker+deploy+plan)<!-- .element: target="_blank" -->
    - [Bid data composer consume issue](http://confluence.vpon.com/display/ADPTM/202107+-+kafka+stream+crach+issues)<!-- .element: target="_blank" -->
    - [Protobuf out of date](http://confluence.vpon.com/display/ADPTM/202109+update+google+protobuf)<!-- .element: target="_blank" --> (from 2.6 to 3.18)
    - [Scalapb ci setting](http://jenkins.vpon.com:8080/job/dsp-common/job/dsp-protobuf-scalapb/)<!-- .element: target="_blank" --> (multi branch)
    - [dsp-reporting swagger](http://dsp-report.vpon.com/doc)<!-- .element: target="_blank" -->


- research & poc:
    - [Redshift migration planning](http://confluence.vpon.com/display/ADPTM/202106+Redshift+db+migration+plan)<!-- .element: target="_blank" -->
    - [Db performance test(clickhouse and postgres)](http://confluence.vpon.com/display/ADPTM/clickhouse+data+poc)<!-- .element: target="_blank" -->
    - cypress application for UI automation[project](https://git.vpon.com/chenghsien.wen/dsp-web-robot-tool)<!-- .element: target="_blank" -->
    - [scala cats](https://chenghsienwen.github.io/scala-cat-execise-docs)<!-- .element: target="_blank" -->
    - [Functional programming in python](https://docs.google.com/document/d/1BGw_iQ3zs9iZkpSKzNLe9sAFMFnDAlL8YXyQKXqyPrk/edit?usp=sharing)<!-- .element: target="_blank" -->



### key contributions
 - features: on schedule and also keep code quality<!-- .element: class="fragment" data-fragment-index="1" -->
- support colleagues: make all flow to be more smooth and keep a positive atmosphere on co-work<!-- .element: class="fragment" data-fragment-index="2" -->
- development refinements: remove technical pain points for further development or testing<!-- .element: class="fragment" data-fragment-index="3" -->
- research & poc: make a easily and reproducible know how and sandbox to furhter real case<!-- .element: class="fragment" data-fragment-index="4" -->


####  example 1 of refinement
- improve TESTING time on CI
- spark is a key conpoment in **report-stramer** project, however, feature tests are not complete for this project
- it would take over *10 minutes* just for few test cases


- before refinement 
![before refinement](mdoc-docs/resources/development_example1_1.png)
<!-- .element: style="width:100%;"  -->


- after refinement
![after refinement](mdoc-docs/resources/development_example1_2.png)
<!-- .element: style="width:100%;"  -->


#### example 2 of refinement
- system integration test to be easier
- if members want to test new feature on bidding, they need to
    - request ad
    - send trackers for accumulating cost and revenue
    - check web console for result


- before
    - members may need to install development env,
        - ex: [protobuf compile tool](https://developers.google.com/protocol-buffers/)<!-- .element: target="_blank" --> for encode/decode
    - send trackers events from ad response
        - parse ad response manually then send URL
    - it would take **many times** to do the same things in UAT


- after
    - online tool for rescue: above tedious things can be avoided in one concole, one click
    - [ad-test-tracker-service](http://ad-test.vpon.com/swagger-docs)<!-- .element: target="_blank" -->
![after refinement](mdoc-docs/resources/UAT_tool.jpeg)
<!-- .element: style="width:100%;"  -->


#### example 3 of refinement
- rebuild native application pipeline
- there was a [native binary tool](https://git.vpon.com/anibal.yeh/segtool)<!-- .element: target="_blank" --> for segments import

- before
    - tool built on Microsoft .Net ecosystem, that is not compatible with others pipeline

- after
    - build pipeline align with current pipeline on jenkins
    - [release template](https://github.com/chenghsienwen/quickstart-scala-sbt-native-image.g8 )<!-- .element: target="_blank" --> for future development


**every refinement/technical debt is small, but accumulation would be far reaching**



## Nobody is perfect, but a Team can be
quotes from: [remember the titans](https://en.wikipedia.org/wiki/Remember_the_Titans)<!-- .element: target="_blank" -->