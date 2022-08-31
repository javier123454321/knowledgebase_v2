# The Continuous Integration/Delivery Lifecycle

## The Problem We are Trying To Avoid
Hey, Dave is on vacation and he usually deploys... how does he do it again?

## Continuous Integration
#### How do we know that the stuff still works
- **Automated Tests**
- **Common Vulnerability Scanning**
- **Sending to a Development Environment** (Has to resemble te architecture of the target machine)

The idea is to get rapid feedback to ensure everything works.

## Pipelines
Break down into Reusable Chunks

Build    ->      Test      ->    Staging      ->       Prod

## Continuous Delivery

Parallel Build/Testin can be done to get different parts of the application

How Do people use my code?

1. Trigger Build
1. Re-Run tests
1. Build application artifacts 
    - Archive File (zip, war, tar)
    - image(Docker, VM Image, AMI)
    - Container
1. Put them Somewhere 
1. Walk away

Delivery is getting the code to a state where it is ready to be deployed
People sometimes combine delivery and deployment

## Continuous Deployment
The How Do I Update The Website Again??

An extra step in continuous delivery. **Actually** Deploying the artifacts.
This is the holy grail of DevOps, a fuly automated and robust build and deploy process.

(Advice, start building trust, keep improving)

## Tooling
- Github Actions
- Jenkins
- Circle CI
- Travis CI
- Azure Pipelines
- AWS CodeStar

## Example Add a Static Site into an S3 bucket

Need to generate a S3 Bucket that has public access permissions and upload a static file. 

