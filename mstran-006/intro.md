![logo](mstran-006/assets/logo-sm.png)

## Objective

The objective of the secenario is to demonstrate a style of representing a microservice using gRPC.

![Data Schema](mstran-006/assets/seats-idl.png)

[gRPC](https://grpc.io/) is an API technology that enables a client and server to communicate by sending streams of data to and fro under [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2). Whereas [RESTful](https://restfulapi.net/) APIs use standard `request/response` sessions to exchange data. gRPC, on the other hand, exchanges data over [bi-directional streams](https://www.programmableweb.com/news/how-to-build-streaming-api-using-grpc/how-to/2020/02/21). Also, the data is by default encoded into a binary format thus facilitating faster communication. The tradeoff is that both client and server must have exact knowledge of data schemas in play prior to communication.

![Basic gRPC](mstran-006/assets/basic-grpc.png)

## What you'll be doing 

In this scenario you'll get the demonstration microservice up and running as a gRPC API. The demonstration microservice is called, *Seat Saver*. The purpose of *Seat Saver* is to allow customers to view, reserve and buy a seats in a given venue. (You worked a vesion of *Seat Saver* written under GraphQL in the previous scenario.)

Once the microservice is running, you'll exercise the code to get a sense of how it works.

You'll be doing the following steps:

* **Step 1:** Installing the lesson code
* **Step 2:** Getting the code up and running
* **Step 3:** Exercising the Code
* **Step 4:** Understanding the Code as an Example a gRPC API.

## Executing command line instructions 

This scenario is completely interactive. The instructions you'll be given will be executed directly in the terminal window that is embedded directly in the Katacoda interactive learning environment. In the steps to come, when you see a command line instruction with a black background and check mark at the end, like so:

![Katacoda command line](mstran-006/assets/command-01.png)

just click on it and the command will execute in the interative terminal window.

Click the START SCENARIO button to start.