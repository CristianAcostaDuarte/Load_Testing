# Load_Testing

## 1. Configuring Docker Desktop.
### Method 1:
- Install Docker Desktop from : [Install Docker Desktop](https://docs.docker.com/desktop/install/windows-install/)!
- To install the wsl distribution run: wsl.exe --install "distribution_name"
  
  <img width="537" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/994eb493-80c8-4b55-91c3-cffdc0b010e0">

- Set up the user and password

  <img width="719" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/485f3166-739b-456c-9715-1fde5968a508">

- At the End you have:

  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/8a646b90-f9b0-41e1-9b36-f055eba6831c">

### Method 2:

- Install WSL from the Microsoft store and Restart:
  
  <img width="772" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/3022b807-f8ef-4edd-a99d-d1f483aab43e">


- At the End you have:
  
  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/740f646c-5ed2-4275-859b-ae7348e20ccc">

## 2. Jmeter Overview.

### Introduction

In JMeter, a test plan is a hierarchical representation of your performance or load testing scenario. It defines the structure and details of your test, outlining various elements, settings, and logic to simulate user interactions and measure application performance. This guide provides an overview of essential components within a JMeter test plan.

### Test Plan Components

#### Test Plan (Top-Level)

- The top-level test plan is the main container for your entire test scenario.
- It contains global settings and configuration options applicable to the entire test, such as thread count, ramp-up time, and loop count.

#### Thread Group

- Thread Groups represent groups of users (virtual users or threads) and define their behavior during the test.
- Attributes like the number of threads, ramp-up time, and loop count are set within a Thread Group.
- Different Thread Groups can simulate various user profiles or scenarios.

#### Samplers

- Samplers are requests or actions simulating user interactions with your application.
- JMeter supports various sampler types, including HTTP requests, FTP requests, JDBC requests, and more, depending on the protocol you want to test.

#### Controllers

- Controllers control test flow and logic.
- Common controllers include:
  - **Simple Controller**: Organizes samplers and other controllers.
  - **Transaction Controller**: Measures response times of grouped samplers.
  - **Loop Controller**: Repeats elements a specified number of times.
  - **If Controller**: Executes elements based on a condition.
  - **While Controller**: Repeats elements while a condition is true.
  - **Switch Controller**: Executes one of several branches based on a condition.
  - **ForEach Controller**: Iterates through a list of values.

#### Listeners

- Listeners are used to view and analyze test results.
- Common listeners include:
  - **View Results Tree**: Displays sample results in a tree-like format.
  - **Summary Report**: Provides summary statistics on test execution.
  - **Aggregate Report**: Offers aggregate statistics on test execution.
  - **Graphs**: Generates various graphs based on test data.
  - **Assertion Results**: Shows results of assertions for response validation.
  - **View Results in Table**: Displays sample results in tabular form.

#### Configuration Elements

- Configuration Elements allow you to configure settings and variables for use throughout the test.
- Examples include the HTTP Cookie Manager, CSV Data Set Config, and User Defined Variables.

#### Timers

- Timers introduce delays or pacing between requests to simulate realistic user behavior.

#### Pre-Processors and Post-Processors

- Pre-Processors run before a sampler, while Post-Processors run after a sampler.
- They can modify request data or extract data from responses.

#### Assertions

- Assertions define criteria for validating response correctness.

#### Test Fragments

- Test Fragments are reusable groups of elements for inclusion in multiple test plan sections.

### Types of Test Plans

There are various types of test plans you can create in JMeter, depending on your testing objectives:

#### Performance Test Plan

- Evaluates performance and scalability under load.

#### Load Test Plan

- Tests performance with a specific load (e.g., concurrent users).

#### Stress Test Plan

- Determines the application's breaking point.

#### Functional Test Plan

- Validates application functionality.

#### Smoke Test Plan

- Basic test to check for critical errors.

#### Data-Driven Test Plan

- Uses external data sources to drive test scenarios.

#### Parameterized Test Plan

- Varies input values dynamically.

#### Distributed Test Plan

- Distributes load across multiple JMeter instances.

The choice of test plan type depends on your specific testing goals and requirements. You can create a combination of these elements within your test plan to meet your testing needs effectively.




## 3. Configuring Jmeter.

- Pull the Dockerfile:
  
  <img width="585" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/81261c74-8597-46a8-89b4-c882dacf6f9e">

- Go to images and run:

  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/184e28d5-463f-4a5a-bf28-ef6a2231fe1c">

### Jmeter Scripts.

- Jmeter comes with a GUI that can't be opened using a Docker container, however Jmeter has support for scripts using .jmx files. Thanks to this approach we are able to introduce our test scripts into CI/CD platforms (Jmeter only recommends the GUI for script creation and Test Debugging).
  
- To create Scripts first download Apache Jmeter in your PC using this guide : [Install Apache Jmeter](https://www.simplilearn.com/tutorials/jmeter-tutorial/jmeter-installation)!

- Go to the Jmeter GUI:
  
  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/5a0053fa-9ee0-4e29-b8de-d73c7935310a">

#### Creating a Simple Test plan: 


##### Add a Thread Group.
- To add a thread group select your Test plan:
  
  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/433a27b6-eb70-4939-80dd-13561f84e049">

- in the Thread Grouo you can define the numbers of VUs (Virtual users), the Ramp up and the Loop count.

  <img width="722" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/8fb0b0c0-8420-4666-83b3-a6957295f230">

##### Add a HTTP Request.

- Select your Thread Group and add a sampler:

  <img width="674" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/7cc0043e-0bcf-4b5c-8e0a-24c1c9281247">

## 4. Configuring Apache Web server.

- Here we want to run a static web app that increase the count every time the user goes to the URL.
  
- Pull the Apache web server image from Docker Hub.

  <img width="613" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/b20b9674-0a98-40c5-85c2-6edb7f9fb851">

- Copy the image name:

  <img width="713" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/1b911bdd-66ef-43ea-8e67-2e23c26c701b">

- Go to the WSL or the ubuntu terminal and use the Docker run command:

  ```shell
  docker run -d -p 80:80 dockerimage
  ```

- Go to localhost:80 to verify your apache web server is running.

<img width="241" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/376430cd-abec-463c-90ba-52cdb55cf823">

- We want to use our own web page so change the default index.html and change it -> Go to your container:

<img width="835" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/5af130e7-0cec-4929-a751-f189aa897c90">

- Use exec to run a commands inside the container.

<img width="378" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/e499ef93-3c0b-4fc6-a9c4-73765706c462">

- Find where the index-html file is located.

<img width="263" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/26fa8eb5-0be9-4426-bef5-8bdf742887c6">

- This is the content of the html file:

<img width="262" alt="image" src="https://github.com/CristianAcostaDuarte/Load_Testing/assets/101611537/6d7571ce-03d4-4899-8fe1-05a8333dcd76">

## 5. Configuring the web app.

- What i did was install VIM in the container and then copy this 

