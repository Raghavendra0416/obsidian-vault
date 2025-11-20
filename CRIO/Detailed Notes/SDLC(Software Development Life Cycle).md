###### SDLC(Software Development Life Cycle)
A **Software Development Lifecycle (SDLC)** is the process used to design, develop, test, and maintain software. It provides a structured way to build high-quality software efficiently and systematically.

for live notes - [[SDLC(Software Development Life Cycle) Note]]

- The **Scrum Master** is not directly responsible for delivering work in any specific SDLC stage (like coding or designing), but instead plays a **facilitative and supportive role across all stages**.
##### **Key Phases of the SDLC**
While the exact number and naming of phases may vary slightly between organizations and SDLC models, the commonly recognized stages are:

##### 1. **Planning and Requirement Analysis**
- **Purpose:** Understand the problem, gather requirements from stakeholders, and define the project’s scope and objectives.
- **Activities:** Stakeholder interviews, feasibility studies, risk analysis, resource allocation, and creation of a Software Requirements Specification (SRS) document.
- **Outcome:** Clear documentation of what the software should do, project timelines, and resource estimates.

##### 2. **Design**
- **Purpose:** Translate requirements into a detailed software architecture and design.
- **Activities:** System architects and designers create high-level and detailed designs, including data models, user interfaces, and system interfaces. Tools like UML diagrams and data flow diagrams are often used.
- **Outcome:** Design documents outlining the system’s structure, modules, and interfaces.

##### 3. **Implementation (Development)**

- **Purpose:** Actual coding and building of the software based on the design specifications.
- **Activities:** Developers write, review, and integrate code, often breaking down tasks into manageable units for efficiency and parallel development
- **Outcome:** Functional software components ready for testing.

##### 4. **Testing**
- **Purpose:** Ensure the software is free of defects and meets the requirements specified.
- **Activities:** Manual and automated testing, bug fixing, validation against requirements, and quality assurance. Testing often runs in parallel with development in modern methodologies.
- **Outcome:** Verified and validated software, ready for deployment.

##### 5. **Deployment**
- **Purpose:** Make the software available for use in the production environment.
- **Activities:** Packaging, environment configuration, installation, and migration of data. Deployment may be gradual (phased rollout) or all at once
- **Outcome:** Software is accessible to end-users.

##### 6. **Maintenance and Support**
- **Purpose:** Ensure the software continues to function as intended after deployment.
- **Activities:** Bug fixes, performance enhancements, security updates, responding to user feedback, and adapting to changing requirements
- **Outcome:** Stable, updated, and improved software over its operational life.


**SDLC Models**

| Model     | Core Characteristics                                         | Typical Use Cases                                  |
| --------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Agile     | Iterative, flexible, customer-focused, rapid feedback        | Projects with changing requirements, startups      |
| Waterfall | Linear, sequential, rigid, well-documented phases            | Small, well-defined projects, clear requirements   |
| DevOps    | Continuous integration/delivery, automation, collaboration   | Cloud solutions, frequent updates, enterprise apps |
| Iterative | Repetitive cycles, incremental builds, evolving requirements | Complex projects, requirements may change          |
| Spiral    | Iterative with risk analysis, customer feedback, prototyping | Large, high-risk, complex projects                 |
| V-Model   | Verification and validation at each stage, structured        | Projects needing strong testing at every phase     |

### Notes:

#### **Stage-by-Stage Walkthrough**
1. **Planning**  
    The Project Manager, Business Analyst, and Product Owner meet to decide the app’s goals, target users, timeline, and budget
2. **Requirements Gathering & Analysis**  
    The Business Analyst interviews potential users (students, professionals) to understand what features are needed (e.g., reminders, task categories), and documents these requirements. The Product Owner ensures these align with business goals
3. **Design**  
    The UI/UX Designer creates wireframes showing how the app will look. The Software Architect designs the backend (database for storing tasks). Developers review the designs to ensure they’re practical
4. **Development (Coding)**  
    Developers build the app’s features, following the designs. The Technical Lead ensures code quality and helps solve technical challenges
5. **Testing**  
    QA/Testers check the app for bugs (e.g., tasks not saving). Developers fix issues. The Product Owner tests the app to confirm it meets requirements before launch
6. **Deployment**  
    The DevOps Engineer prepares the app for release and publishes it to app stores. The Project Manager coordinates the release schedule
7. **Maintenance**  
    After launch, Developers fix bugs and add new features based on user feedback. The Support Team assists users with problems. The Product Owner decides which updates are most important

#### Summary Table: SDLC Stages and Responsibilities

|Stage|Main Responsible Roles|
|---|---|
|Planning|Project Manager, Business Analyst, Product Owner|
|Requirements|Business Analyst, Product Owner, Stakeholders/Users|
|Design|UI/UX Designer, Software Architect, Developers|
|Development|Developers, Technical Lead|
|Testing|QA/Testers, Developers, Product Owner|
|Deployment|DevOps Engineer, Project Manager, Developers|
|Maintenance|Developers, Support Team, Product Owner|

| **Role**               | **Main Responsibilities**                                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Project Manager        | Plans, leads, manages scope, timeline, budget, and team; communicates with stakeholders                                |
| Program Manager        | Oversees multiple projects, aligns them with organizational strategy, manages resources, risks, and stakeholders       |
| Product Owner          | Defines product vision, prioritizes features and backlog, represents customer/stakeholder interests, ensures value     |
| Business Analyst       | Gathers and documents requirements, analyzes business needs, bridges communication between stakeholders and team       |
| Designer (UI/UX)       | Translates requirements into designs, creates wireframes and prototypes, ensures usability and user experience         |
| Developer              | Designs, codes, tests, debugs, documents, and maintains software                                                       |
| Manual Tester          | Writes and executes test cases, finds and reports bugs, verifies fixes, ensures software quality                       |
| QA Automation Engineer | Develops automated test scripts, executes automated tests, maintains automation frameworks, ensures continuous quality |
| DevOps Engineer        | Automates deployments, manages CI/CD pipelines, infrastructure, monitoring, and security                               |
| Scrum Master           | Facilitates Agile process, coaches team, removes blockers, leads Agile ceremonies (e.g., stand-ups, sprint planning)   |

---
#### Story of SDLC with an example:

Once upon a time, a team set out to build a simple To-Do List mobile app. Their journey followed the steps of the Software Development Life Cycle, with each member playing a key role.

First, the Project Manager, Business Analyst, and Product Owner gathered in a meeting room. They discussed what the app should achieve, who would use it, how long it would take, and how much it would cost. They mapped out the vision, making sure everyone was on the same page.

Next, the Business Analyst went out to talk to real people—students and professionals—asking what features they wanted in a to-do list app. Should it have reminders? Task categories? The Analyst carefully documented these wishes. Meanwhile, the Product Owner checked that these ideas matched the overall business goals, ensuring the app would be both useful and viable.

With a clear list of requirements, the UI/UX Designer began sketching how the app would look and feel, creating wireframes for the team to review. The Software Architect designed the technical side, planning how tasks would be stored in the backend database. Developers joined in, reviewing the designs to make sure they were realistic and ready for coding.

The development phase began. Developers started building the app, turning designs into real features—adding, editing, and deleting tasks. The Technical Lead watched over the process, making sure the code was clean and helping solve any tricky problems that came up.

Once the app was built, it was time for testing. QA testers tried out every feature, looking for bugs—like tasks that wouldn’t save or reminders that didn’t ring. Developers fixed the issues they found. The Product Owner gave the app a final check, making sure it worked as promised.

When the app was ready, the DevOps Engineer took charge of releasing it to the app stores. The Project Manager coordinated the launch, making sure everything went smoothly and on schedule.

Even after launch, the story didn’t end. Developers continued to fix bugs and add new features based on user feedback. The Support Team helped users with any problems. The Product Owner listened to feedback and decided which updates would make the app even better.

And so, the team’s journey through the SDLC ensured their simple To-Do List app was built with care, teamwork, and continuous improvement.
