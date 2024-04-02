---
layout: default
title: Project
---

# Project: C++ REST API

## Project Description

This project aims to provide hands-on experience in designing and implementing a REST API using the Crow framework, a high-performance C++ micro web service framework. Teams will have the creative freedom to propose their own REST API ideas. 

This project presents an opportunity for teams to creatively explore API development, leveraging the power of C++ and Crow, while also emphasizing the importance of design, testing, and documentation in software development.

## Instructions

1. Complete all of the work in a Group GitHub repository: [https://classroom.github.com/a/OponNjH6](https://classroom.github.com/a/OponNjH6)
2. __Name your group using a combination of the first names of the group members.__ 

## Team Formation

#### Team Size: 
* 2 members per team

#### Roles and Responsibilities: 

* Team members should __share roles for all project aspects__ like design, coding, testing, and documentation.


## Part 1: Team Creation and Proposal

### Due:  Thursday April 4th

#### Task: 
* Each team will brainstorm and propose an idea for a REST API. 
* The idea shall be feasible and provide clear value to potential users.
* The idea shall be complex enough to have a __minimum of four resources (aka. classes/object types)__.


#### Deliverable: 
* A brief proposal document outlining the API concept.
* Add this proposal to the `README.md` file in your project GitHub repository.
* Add the names of your team members to the `README.md` file in your project GitHub repository. 


## Part 2: Design Document Creation

### Due: Friday April 12th

* Create a detailed design document for the proposed API. 
* The document should include:
    - __Introduction__: An overview of the API and its purpose. 
    - __Background/Context__: The problem or need the API addresses.
    - __Stakeholders__: Identify the parties interested in or affected by the API.
    - __Functional Requirements__: A clear and detailed description of what the service will do.
    - __Use Case Description__: Describe __all__ the interactions between users and the system. This can be in the form of user stories. For example, “As a customer, I want to view book reviews and ratings before purchasing, so that I can make informed decisions.”
    - __List Of Resources__: A list of the resources available from your API, with a description of each resource.
    - __List of End Points__: A list of REST endpoints that your API will provide to users. Make sure to include the URL, the HTTP method (GET, POST, PUT, DELETE), the request BODY (if any) and request parameters (if any). Provide the expected response including the response BODY (if any) and HTTP status code. Provide your error handling strategies and expected HTTP error codes.
    - __UML Diagrams__: Create a class diagram outlining the main classes and their relationships.
  
#### Deliverable:   
* A comprehensive design document as described above. 
* Add your design document to the file `DESIGN.md` in your project GitHub repository.

## Part 3: Implementation

### Due: Friday April 26th 

* Implement the API in C++ using the Crow framework.
* Develop the RESTful API endpoints as per the design document.

#### Requirements:
1. The implementation shall have a minimum of __four classes__.
2. The implementation shall demonstrate a minimum of one __instance of composition__.
3. The implementation shall demonstrate a minimum of one __instance of inheritance__. 
4. The implementation shall demonstrate a minimum of one __instance of templates__.
5. The implementation shall __save the resources to a file__ after the Crow app is stopped.
6. The implementation shall __read the resources from a file__ before the Crow app is started.  
7. The implementation shall __include a Makefile__ with an all, clean, executable, and individual targets for each cpp file. 


#### Deliverable:
* A functioning REST API.
* All the code needed to run your API should be included in the project GitHub repository.
* A Makefile that will build each component of the API, and the executable file.

## Part 4: Unit Testing

### Due: Friday April 26th

* Develop a suite of unit tests using a testing framework.
* __Testing Scope__: Cover all critical functionalities and endpoints.

#### Deliverable:
* A comprehensive unit testing suite ensuring the reliability of your code.
* All the code needed to run your unit tests should be included in the project GitHub repository.


## Project Grading Rubric

### Part 1: Team Creation and Proposal (Total: 5 points)

#### Clarity and Quality of Proposal (5 points)
- [ ] 0 points: Idea is not feasible, lacks clarity, or no clear value to users.
- [ ] 1-2 points: Idea is somewhat feasible or provides unclear value to users.
- [ ] 3 points: Idea is feasible and provides some value to users.
- [ ] 4 points: Idea is feasible with a clear value proposition and meets minimum complexity requirements.
- [ ] 5 points: Idea is innovative, feasible, complex enough, and offers a compelling value to potential users.

### Part 2: Design Document Creation (Total: 25 points)

#### Comprehensiveness of Design Document (10 points)
- [ ] 0-3 points: Missing significant sections or details.
- [ ] 4-6 points: Contains all sections with minor omissions or lack of clarity.
- [ ] 7-8 points: Most sections are complete and detailed.
- [ ] 9-10 points: All sections are complete and detailed.

#### Use Case Descriptions (5 points)
- [ ] 0-1 points: Use cases are not clear or are missing.
- [ ] 2-3 points: Use cases are present but lack detail.
- [ ] 4-5 points: Use cases are detailed and provide clear insight into user interactions.

#### List of Endpoints (5 points)
- [ ] 0-1 points: Missing endpoints or critical details (HTTP methods, parameters, etc.).
- [ ] 2-3 points: Endpoints are listed with some details missing or unclear.
- [ ] 4-5 points: Endpoints are clearly listed with detailed request/response and error codes.

#### UML Diagram Quality (5 points)
- [ ] 0-1 points: UML Diagram is missing, incomplete, or incorrect.
- [ ] 2-3 points: UML Diagram is present with inaccuracies or lacks clarity.
- [ ] 4-5 points: UML Diagram is accurate, detailed, and clearly represents the system.

### Part 3: Implementation (Total: 50 points)

#### Implementation of Classes and Relationships (15 points)
- [ ] 0-4 points: Fewer than four classes or missing key relationships (composition, inheritance).
- [ ] 5-9 points: Meets minimum class count with basic implementation of composition and inheritance.
- [ ] 10-12 points: Four or more classes with correctly implemented composition, inheritance.
- [ ] 13-15 points: Four or more classes with well-implemented composition, inheritance, and templates.

#### Data Persistence (10 points)
- [ ] 0-3 points: Does not save/read resources to/from a file, or implementation is flawed.
- [ ] 4-6 points: Saves/reads resources with minor issues.
- [ ] 7-8 points: Saves and reads resources with minor improvements needed.
- [ ] 9-10 points: Flawlessly saves and reads resources to and from a file.

#### Makefile and Build Process (10 points)
- [ ] 0-3 points: Makefile is missing, incomplete, or does not work.
- [ ] 4-6 points: Makefile is present with minor issues in the build process.
- [ ] 7-8 points: Makefile is functional with room for optimization.
- [ ] 9-10 points: Makefile is fully functional with all, clean, executable, and individual targets.

#### Functionality of REST API (15 points)
- [ ] 0-4 points: REST API is non-functional or severely flawed.
- [ ] 5-9 points: REST API is functional with some issues.
- [ ] 10-12 points: REST API is functional and meets most design specifications.
- [ ] 13-15 points: REST API is fully functional, meets all design specifications, and demonstrates advanced features or exceptional quality.

### Part 4: Unit Testing (Total: 20 points)

#### Coverage and Depth of Testing (10 points)
- [ ] 0-3 points: Tests are missing or cover only a small portion of functionalities.
- [ ] 4-6 points: Tests cover a substantial portion of functionalities but lack depth.
- [ ] 7-8 points: Tests are comprehensive, covering most critical functionalities in depth.
- [ ] 9-10 points: Tests are exhaustive, covering all critical functionalities and edge cases in depth.

#### Quality and Reliability of Tests (10 points)
- [ ] 0-3 points: Tests are unreliable, frequently produce false positives/negatives.
- [ ] 4-6 points: Tests are mostly reliable with occasional inaccuracies.
- [ ] 7-8 points: Tests are reliable and thorough with only minor improvements needed.
- [ ] 9-10 points: Tests are reliable, thorough, and consistently accurate, reflecting best practices in testing.
