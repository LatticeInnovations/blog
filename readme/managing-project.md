# Managing project

## **Managing projects**

Have you faced a situation where a project appeared to be in control for the first two-thirds, and then spiraled out of control close to the finish line? This has happened to us more times than we would like to remember.&#x20;

Our response has been to develop work practices that prevent some of these situations from occurring, through better planning and error prevention.

## Definitions first

Who is a manager? Someone who plans, and addresses deviations from the plan. Without plans, deviations cannot exist. As deviations decrease, so does the need for managers.

What is a project? A set of interconnected tasks that, once complete, achieves a goal.

Thus, to manage (or supervise) a project, is to select a goal, plan to achieve it, and address deviations that arise on the way.

## Planning a project

Our project planning process is divided into four steps.

1. List and categorize all the tasks that must be completed to reach the goal.
2. Sequence tasks in the order in which they must be performed.
3. Allocate tasks and estimate their duration, based on the resource[^1] who will perform them.
4. Schedule based on the resource’s availability and capacity.

**When all four steps are complete, a project plan can be visualized as a Gantt chart.**

### List

Though simple, a comprehensive list of tasks is essential — otherwise the project is sure to deviate. While listing tasks, we work from the finish to the start. This puts us in a delivery-centric mindset, and reduces the risk of missing a task.

Error prevention also starts here. As we made more project plans, we built a master template. An exhaustive template only has to be trimmed down to suit a particular project. It is much easier to whittle down a list, than to remember what to add. This also applies to making a list for packing clothes for a trip. Make a 7-day-trip version first, and then trim it for a weekend trip.

### Categorize

A task is categorized by the workstation that performs it, and the component[^2] that it belongs to.

A component is a portion of the project that can be developed independently. For instance, a mobile app for primary healthcare may have the following components—user registration and login, screening, consultations and prescriptions.

Design and development of such an app involves six workstations—scoping, system specifications, user interface design, backend coding, frontend coding, and final inspection[^3].

Tasks are thus labeled with both their workstation, and the component. And work flows from one workstation to another, for each component, until all components are complete, and ready for final assembly into a single app.

### Sequence

Sequencing requires us to understand dependencies between tasks.

There are 2 types of dependencies — workflow-driven, and resource-driven. Workflow-driven dependencies arise from the need to do work in a particular sequence — backend services are required for frontend application code to work. Resource-driven dependencies arise when the worker has to finish one task before starting the next.

Once we label a task with its workstation and component, the workflow-driven dependencies become clear.

Resource-driven dependencies are readily apparent—we use a software tool that totals up the workload on each member of our team, to ensure that resource-driven dependencies are accounted for. Recently, we developed a system to enable cross-project dependency checking.

To deskill task sequencing, we create templates that provide workflow-based dependencies.

### Allocate tasks, estimate duration

When tasks are performed manually[^4], task duration is intimately tied to allocation. The more capable a contributor, the lower the duration.

Tasks are sufficiently granular so that they can be allocated to one individual. This brings in accountability. Two people cannot chop vegetables using the same knife.

### Schedule tasks

Once we have estimated durations for each task, we add them up by contributor. The contributor who is the most heavily loaded, limits the rate at which work can be completed. This is the busy bee.

For the project team to deliver at the highest rate possible, the busy bee must be kept fully occupied—though not overloaded! Hence, all other contributors’ schedules must be subordinate to the busy bee’s. Also, the busy bee’s schedule has to be protected by the entire project team. To do so, other team members have to treat any work flowing to the busy bee with the highest priority.

Before finalizing the schedule, it is often useful to check if some of the busy bee’s tasks can be assigned to other team members. This is called load leveling.

Once we make the schedule, we examine the critical path, i.e. the longest path that determines project duration. It must include all the tasks to which the busy bee is allocated. If not, the schedule is likely erroneous.

A well-laid out schedule enables each contributor to see their own task sequence, along with immediate predecessors and successors.

### Add a buffer

The final step of creating a project plan is to include a project buffer—a measure of uncertainty. Uncertainty has three drivers:

1. Task complexity: the harder each task, the greater the uncertainty.
2. Interdependence: the more intertwined the tasks, the greater the uncertainty.
3. Project duration: the longer the project, the more it amplifies the first two drivers.

At Lattice, we use a simple heuristic to calculate the project buffer. We assign a score of 1, 2 or 3 — corresponding to low, medium or high — to complexity and interdependence. We then sum them up, and multiply the result by the project duration, in months, to arrive at the buffer duration, in days.

Thus, a complex, medium-interdependence, two-month project has a buffer of 10 days. In contrast, a simple, low-interdependence project lasting a month has a buffer of 2 days.

Often, clients view a project buffer as a place to “save time”. But deleting the buffer does not magically remove uncertainty. Project managers need the support of senior managers to protect project buffers.

## Tracking & resolving deviations

Thus far, our focus was on creating a plan. Once we begin executing it, we have to check for deviations, and act to correct them. This represents the third and fourth steps of the PDCA loop—plan, do, check and act.

### Identifying deviations

The project buffer is a single metric that reveals deviations. Suppose the project has progressed by 25%, but 50% of the buffer has been used up. This warns us of deviations that can result in late completion of the project.

### Sources of deviation

The project planning process itself suggests the following sources of deviations:

1. Task missed
2. Task mis-sequenced
3. Task mis-allocated
4. Task duration higher than planned, because of any one of the following:
   1. time taken to fix errors or defects
   2. an erroneous estimate of task difficulty
   3. an erroneous estimate of contributor’s capability
   4. delays in starting or doing the work

Only the last source of deviation is person-dependent; all others are process-related. Hence, managers are best served by improving processes. As process-related errors are eliminated, person-dependent errors shrink rapidly. A workplace that eliminates waste from its processes, provides an environment that encourages its workers to improve their performance. A waste-free environment encourages waste-free habits[^5].

The surest way to reduce process-related errors is through the use of work standards, which is a key weapon in Kaizen’s armory.

Once we implement work standards, our PDCA loop transforms into an SDCA loop. Each time we work on a project, we standardize[^6] what we learn by updating our work standards. We must be aggressive in culling down work standards to only those that are necessary, else we run the risk of creating bureaucratic overhead. If a new work standard is not updated in 6 months from its date of creation, it should be consigned to the rubbish heap. No one is using it.

Work standards provide a mechanism by which the lessons learnt by one project team can be shared with many. Learning from our own errors is experience. Learning from others’ errors is wisdom.

## Further reading

In the next post, "Finding the critical path", we dive into how to identify the critical path in a project—a essential aspect of of scheduling tasks, and a diagnostic tool for analyzing deviations.

[^1]: There are 3 types of resources — supplies, equipment and people. For most services businesses, like Lattice, resources equal people.

[^2]: **At Lattice, we prefer to use “module” while referring to products and solutions, and “component” while referring to the process of assembling them. Modular products are enabled by componentized design and development. In casual conversation, though, I use these two terms interchangeably.**

[^3]: We have a final inspection workstation today. We have to work towards eliminating it.

[^4]: **Merely using a tool does not make a task automated. Software development is manual — a contributor’s capability determines the rate of work.**

[^5]: **Just like a litter-free environment encourages us to throw trash in the trash can. Environments have a profound influence on our behavior — this has to be understood by managers and leaders to create any organizational change.**

[^6]: **The term “standardize” is often misunderstood. It brings to mind monotonous, repetitive work. But doing the same thing is not standardization. Rather, to standardize is to transform fluctuating inputs into consistent output.**
