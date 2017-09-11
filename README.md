# Cloud Compute POC

## Overview

The goal of this POC is to evaluate the anticipated technological, operational and economic efficiencies of a 
hybrid infrastructure architecture for a risk and pricing platform that would essentially entail running the platform's 
compute on public cloud and in turn assess approaches for the following core aspects of cloud computing:

 * Ease of on-boarding measured by facilities for integration with and extension of on-prem infrastructure onto the 
   public cloud leveraging industry standard protocols for compute, network and data security with identity management 
   and role based access control of resources
 * Efficient, version controlled and automated provisioning of Infrastructure as Code
 * Continuous Integration, Deployment and Delivery pipelines facilitating immutable infrastructure and in turn support 
   for blue/green deployments and ease and agility of rollbacks
 * Schedule and Metrics driven Elasticity of Compute
 * Efficiency of scheduling and management of resources in an environment with virtual multi-tenancy - running container 
   virtualized workload along side native non-container workload on a shared infrastructure
 * Management of application, system and audit logs with support for metrics monitoring and alerting   
 * Economy of provisioning, operating and scaling the infrastructure footprint on-demand in the context of aspects
   delineated above
 * Granularity of usage metering, transparency of pricing and chargeback and flexibility of account/subscription 
   management 
   
   
## Mock Compute Engine

### Description

Mock Compute Engine essentially mimics the semantics of one of platform's core compute engines by mocking pricing compute 
leveraging a trivial [Java Wrapper](https://github.com/amolthacker/azure-poc-compute-engine-mock) around [QuantLib](http://quantlib.org/index.shtml), 
an open-source quantitative library, for a subset of metrics as follows:
 * FwdRate  : Spot price of a sample Forward Rate Agreement
 * NPV      : Net Present Value of a Vanilla Fixed/Float Interest Rate Swap
 * OptionPV : Price of Put Option averaged over multiple methods (Black-Scholes / Monte-Carlo etc.)
      

The Mock Compute Engine application's implemented with the following flavors so as to help evaluate and identify the 
optimal architecture for an elastic compute on Azure:

 * [Simple RPC   : Using Azure VM Scale Sets](https://github.com/amolthacker/azure-poc-compute-engine-vmss) with [CI/CD pipeline](https://github.com/amolthacker/azure-poc-compute-engine-vmss-cicd)
 * [Simple RPC   : Container orchestrated with Kubernetes in ACS](https://github.com/amolthacker/azure-poc-compute-engine-acs-rpc)
 * [Akka Cluster : Container orchestrated with Kubernetes in ACS](https://github.com/amolthacker/azure-poc-compute-engine-acs-akka)
 * [Apache Spark : Container orchestrated with Marathon on Apache Mesos in DC/OS in ACS](https://github.com/amolthacker/azure-poc-compute-engine-acs-spark) 
