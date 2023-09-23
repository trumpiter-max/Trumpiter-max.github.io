---
title: "Project"
permalink: /project-management/fundamental/project
excerpt: "A group of tasks that need to complete to reach a clear result"
---

# Prerequisite

There are *3 needs* for managing project:

- Time.
- Cost.
- Quality.

## Some importance of project management

- Achieving Goals and Objectives.
- Efficient Resource Utilization.
- Risk Management.
- Communication and Collaboration.
- Continuous Improvement.

## Project life cycle

The *common project life cycle (CPLC)* phases are as follows:

- **Initiation** - objectives, scope, stakeholders, and high-level requirements are identified.
- **Planning** - define tasks, schedules, resource allocation, budget, and risk management strategies.
- **Execution** - regular communication, monitoring, and control of the project's progress ensure that the project stays on track.
- **Monitoring and Controlling** - involve tracking tasks, assessing risks, managing changes.
- **Closing** - finalized, reviewed deliverables and administrative tasks, such as documentation, financial closure, and transition to operations.

From above life cycle, for software developement, the **software development lifecycle (SDLC)** is the cost-effective and time-efficient process that development teams use to design and build high-quality software:

- **Requirement analysis**: proposal, planning, SRS.
- **Design**: high (system architecture, database ER) & low (dataflow, datastructure, sequence diagram) level design. 
- **Implementation**: identify smaller coding tasks.
- **Testing**: automation and manual testing to check the software for bugs.
- **Deploy**: move the latest build copy to the production environment.
- **Maintain**: configures, fix bugs, resolve customer issues, create user guides, and manage software changes.

# Approach

There are 3 factors to choose suitable approaching work model:

- Project type.
- Size of teams.
- Time for project.

## Traditional

![Waterfall](/assets/images/collection/sdlc_waterfall_model.jpg)

**Waterfall** is old traditional methodology (**linear progression** from beginning to end) to develope products because it is easy to use, **fixed-cost** but there is still some drawbacks:

- *Less flexible* making projects slower if having any changes in process.
- Need *clear requests/constraints/timeline* from clients.
- Need a lot of times for planning, designing.

## What is agile

![Agile](/assets/images/collection/software-engineering-agile-model.png)

The **iterative** and **people-centric** approach prioritizes **estimated-cost**, *quick delivery*, adapting to change, and collaboration rather than **top-down management** and following a set plan being carried out in *short-term development* cycles.

![Values](/assets/images/collection/agile-value.png)

If a project doesn’t have clear constraints, timelines, or available resources, it’s a good candidate for an Agile approach.

![Principles](/assets/images/collection/12-agile-principles.png)

### Some benefits

- Increased collaboration.
- Better alignment to business needs.
- Project risk reduction.

### Some drawbacks

- Organizations can resist change in adoption.
- Inadequate training or education.
- Not enough leadership participation.

### Application

#### Planning

- **User story** is the smallest unit of work. It's an end goal, not a feature.
- **Product backlog** refers to a prioritized list of functionality which a product should contain.
- Estimation techniques: Planning Poker, Relative Sizing.
- Story points and velocity.
- Release planning and iteration planning.

#### Development practices

- Test-driven development (TDD).
- Continuous integration and continuous delivery (CI/CD).
- Pair programming and code reviews.
- Retrospectives and process improvement.

#### Scaling

- Some scaling frameworks (e.g., SAFe, LeSS, Nexus).
- Challenges in scaling Agile.
- Agile at the portfolio level.

## What is scrum

![Scum](/assets/images/collection/scum.png)

Scrum is an **empirical process**, where decisions are based on observation, experience and experimentation. Scrum has three pillars: **transparency**, **inspection** and **adaptation**.

The **Scrum values** of **Courage**, **Focus**, **Commitment**, **Respect**, and **Openness** binding all of the elements together is **Trust**.

### Some benefits

- **Flexibility** allows teams to adapt to changing requirements and priorities.
- **Transparency** promotes transparency at all levels. This enables the team to incorporate customer feedback early and often, leading to higher customer satisfaction.
- **Early delivery of value** increases in short iterations.
- **Predictability** provides a predictable rhythm with its fixed-duration sprints.

### Some drawbacks

- **Rigidity** for some projects can be limit projects that require more flexible timelines.
- **Inaccurate initial estimates** makes the effort required for each item can be challenging, leading to inaccurate predictions for sprint outcomes.
- **Overemphasis on meetings** can become time-consuming if not managed efficiently, potentially taking away from productive development time.
- **Risk of burnout** can sometimes lead to burnout among team members if not properly managed.

### Sprint

#### Sprint point

To estimate the amount of effort it will take to complete an item in the backlog.

Some methods to calculate point of tasks:

- **Linear**: 1 (extra small), 2 (small), 3 (medium), 4 (large), 5 (extra large).
- **Powers of 2**: 1, 2, 4, 16, ...
- **Fibonacci**: 1, 2, 3, 5, 8, 13, 21, ...

**Note**: a task which high points should be splitted into multiple smaller tasks.

#### Daily standup

The developer team should to talk around three questions:

- What did you do yesterday to help to achieve the Sprint Goal?
- What will you do today?
- What prevent us from achieving the Sprint Goal?

#### Sprint review

To get feedbacks from main stakeholder and analyze what to do next sprint.

#### Sprint retrospective

To reflect on what went well and what could be improved for their next sprint.

## What is kanban

![Kanban](/assets/images/collection/kanban.jpg)

A **scheduling system** limits the buildup of excess inventory at any point in production. **Problem areas** are highlighted by measuring lead time and cycle time of the full process and process steps.

### Some benefits

- **Visual management** relies on visual boards that depict the workflow and the status of each work item providing transparency, and the current state of tasks, bottlenecks.
- **Work items** are typically small and are completed as they move through the workflow, allowing for quicker value delivery.
- **Efficient resource utilization** identifies bottlenecks and allocate resources more effectively that makes decisions about how to best complete their work. This empowerment can lead to increased engagement and ownership among team members.
- **Metrics-driven improvement** relies on data and metrics to drive improvement efforts.

### Some drawbacks

- **Lack of structure** might lead to confusion or inefficiency.
- **Risk of over-optimization** can sometimes lead to micro-optimizations at the expense of larger process improvements. Teams might focus on reducing bottlenecks without addressing underlying issues.
- Requires **high level of discipline** makes teams need to maintain a high level of discipline to ensure that work flows smoothly and that the Kanban board accurately represents the current state of tasks.
- **Dependence on strong team communication** relies heavily on team members communicating and collaborating effectively.

### Principles

- **Visualizing** work with *time-boxing* techniques.
- Limiting **work in progress**.
- Managing flow.
- Making process policies explicit.

### Components

- **Kanban board** is a visual representation of the workflow divided into columns that represent different stages or steps in the work process.
- **Columns** represent the stages or states that work items pass through. These could include stages like "To Do", "In Progress", "Testing", and "Done".
- **Work items** are represented by cards on the Kanban board. Each card represents a task, feature, or user story. Work items are moved across columns to visually indicate their progress.
- **Work-In-Progress (WIP)** limits are set for each column to control the number of work items that can be in progress at any given time. WIP limits prevent overloading the team and help maintain a smooth flow of work.
- **Swimlanes** are horizontal sections on the Kanban board that can be used to group work items by different categories: priority levels, or types of work, ...
- **Visual signals** are often used to indicate the status of work items including color-coded cards, icons, or other visual cues to represent different types of work, urgency, or other relevant information.
- **Pull-based system** means that new work is pulled into the system only when there's available capacity to handle it. This prevents overloading the team and ensures a more manageable workflow.
- **Continuous improvement** analyzes their workflow, identify bottlenecks, and make incremental changes to optimize their processes.
- **Feedback loops** address issues and gather insights to help the team discuss work in progress, upcoming work, and potential improvements.
- **Explicit policies** promotes the use for each column defined the criteria that must be met for a work item to move from one column to the next, ensure consistent workflow management.
- **Metrics and analytics** includes cycle time (how long it takes for a work item to move through the workflow) and lead time (total time from request to completion).
- **Service level agreements (SLAs)** can be used to define the expected timeframes for work items to move through specific stages.
