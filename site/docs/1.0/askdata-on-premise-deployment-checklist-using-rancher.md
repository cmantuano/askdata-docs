---
title: Askdata On-Premise Deployment Checklist (using Rancher)
keywords: documentation
last_updated: October 15th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
layout: docs
---

**Askdata On-Premise Deployment Checklist** (using Rancher)  

**1. Requirements:**  


1. Rancher Kubernetes Manager (recommended version 2.2.4, helm 2.16.5)
2. Creation of Load balancer that will be used as a single point entry for the application
3. Creation of Kubernetes Cluster

Sizing: Minimum 3 nodes. 8 Virtual CPU, 32GB RAM for each node  

**2. Deployment tasks:**  


1. Configure Rancher adding the Askdata catalog to your Rancher instance with a private credentials
2. From the Askdata catalog install MongoDB application (Askdata helm chart)
3. From the Askdata catalog install Elastic (Askdata helm chart)
4. From the Askdata catalog install Kafka (Askdata helm chart)
5. From the Askdata catalog install the Askdata platform
6. From the Askdata catalog install Airflow (Askdata helm chart)  

**3. Identity Custom Integration:**

In case of deployment of a custom OAuth2 authentication - it will be required to develop and deploy, on the same cluster, a custom Oauth2 microservice to handle Single Sign-on authentication request according to the security requirements of the target environment  

**4. Fully managed alternative:**  

The Askdata team can connect our Rancher instance directly to the target Kubernetes cluster deployed on your datacenter to reduce the Operation maintenance activity on the customer side. The connection between Rancher and the cluster can be secured using a VPN site-to-site. This second scenario will reduce the operations support you have to provide to manage and run Askdata.

{% include links.html %}
