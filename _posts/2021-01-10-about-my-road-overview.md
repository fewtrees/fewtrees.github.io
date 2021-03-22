---
title: What is AboutMyRoad
tags: [AboutMyRoad, front-End, react-native, graphql, kubernetes, docker]
style: fill
color: success
description: AboutMyRoad project overview
---

AboutMyRoad is a project to deliver official data from the UK government into the hands of mobile phone users. The app satisfies the need of people who choose to make an informed choice towards deciding on a location given their wants or needs.

Some example screens..
<div class="row">
  <div class="col-12 col-sm-3">
    <img src="/assets/images/appstore_screenshot_school.png">
  </div>
  <div class="col-12 col-sm-3">
    <img src="/assets/images/appstore_screenshot_school_filter.png">
  </div>
  <div class="col-12 col-sm-3">
    <img src="/assets/images/appstore_screenshot_school_data.png">
  </div>
</div>

<br/>
The project currently publishes the following information:

| **Area of interest** | **Provided by** |
|-----|-----|
| Primary Schools | Ofsted|
| Secondary Schools | Ofsted |
| Nurseries | Ofsted |
| Doctors | Care Quality Commission |
| Hospitals | Care Quality Commission |
| Carehomes | Care Quality Commission |
| Health Clinics | Care Quality Commission |
| Restaurant Hygiene Rating | Food and Standards Agency |
| Flooding Areas | Department for Rural Affairs |
| Crime Statistics | UK Police |
| Age Demographics | UK Census Data |

<br/>
The app uses mapping from either <a target="_blank" href="https://maps.google.com">google maps</a> or <a target="_blank" href="https://www.apple.com/uk/maps">apple maps</a>  together with  geographical data to produce a map of locations with ratings and other important data. Users interact with the information provided to further  uncover details about their chosen interests.

This is the only app that has brought together a multitude of government data in a consistent user experience and prevents the need to search out lots of sources and attempt to integrate the results.

## Application Implementation

The system is delivered in 2 parts, the first is a mobile UI and the second is a <a target="_blank" href="https://kubernetes.io">kubernetes</a> architecture deployed in the cloud.

<br/>
##### Mobile Application

<div class="row">
  <div class="col-3">
    <img class="d-inline-block" src="/assets/images/appstore_screenshot_flood.png">
  </div>
  <div class="col-9">
    <p class="m-10"><br/>The UI uses <a target="_blank" href="https://reactnative.dev">react-native</a>, a mobile app framework that runs on both iOS and Android with very little functional compromise. A framework that is cross-platform can suffer from being the lowest common denominator but given our simple UI approach react proved to be extremely capable. <a target="_blank" href="https://reactnative.dev">react-native</a> is produced by Facebook and is widely used amongst the industry. 3rd party support for <a target="_blank" href="https://reactnative.dev">react-native</a> is also high and receives enthusiastic attention from a large developer community.</p>
  </div>
</div>
<br/>
##### Cloud Services

A <a target="_blank" href="https://kubernetes.io">kubernetes</a> architecture coupled with <a target="_blank" href="https://www.docker.com">docker</a> containers provides a horizontally scalable environment that's easy to monitor and size according to demand.

<div class="row d-flex justify-content-center">
  <div class="col-12 col-sm-8">
    <img src="/assets/images/amr_kubernetes.png" alt="A simplified diagram">
    <figcaption class="figure-caption text-center">Simplified kubernetes components</figcaption>
  </div>
</div>

<br/>
Every component is deployed as a <a target="_blank" href="https://www.docker.com">docker</a> container and configuration of each container function is external. As there are no component changes between a development or production environment, continuous delivery pipelines can easily promote docker images between environments. 

Server-side components were written in Java and form a utilitarian part of the implementation. <a target="_blank" href="http://geoserver.org">Geoserver</a> provides a tile-mapping service that is supplied data from a <a target="_blank" href="https://postgis.net">PostGis/postgres</a> database. Given the plethora of datasources a lightweight framework was written to allow dynamically choosing the datasource for specific geographic data.

<a target="_blank" href="https://www.nginx.com">nginx</a> was employed to proxy map requests and provides a rudimentary cache although this is likely to change for a geospatially aware WMS proxy offering greater flexibility.








