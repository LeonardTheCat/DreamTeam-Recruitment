# MANOR RACING - Software Engineering Tech Test

Thanks for your interest in Manor Racing! 

Our technical test consists of a short coding challenge, followed by some additional excercises.

We have provided a C# [ASP.Net Core 1.0](https://blogs.msdn.microsoft.com/webdev/2016/06/27/announcing-asp-net-core-1-0/) based Web.Api 2 project as a starter. Please feel free to roll your own project from scratch if you want.





## Coding challenge

### What is it?
The subject of the coding challenge is an incomplete Web.Api 2 project, providing access to Car Telemetry data. 
We have provided sample data ``telemetry.json`` for you to use as a base.

### What do I need to do?
1. Ensure that you have [ASP.Net Core 1.0](https://blogs.msdn.microsoft.com/webdev/2016/06/27/announcing-asp-net-core-1-0/) installed.
2. Clone or download this repository.
3. Code!

As a minimum, please implement stories [MR-001](#story-mr-001) and [MR-002](#story-mr-002). 
It is recommended that you implement one (or more) of the [additional stories](#additional-stories) to make your application competitive.

**Please ensure your check-in notes contain the Story # that you are working on.**

### How long does it take?
There is no time limit for this excercise - we just ask that you commit _little and often_ so that we can see the evolution of your solution.

### Submission details
Due to email attachment size limits, we have set up some shared storage for taking submissions.

- Once you have completed the test, please email software-jobs@manorracing.com and you will be provided with an invite for access to shared storage.
- Upload your solution and it will be reviewed by a member of our team.


---

### Story MR-001

> "_As a **Vehicle Science Engineer**_ 
> _I want to **view recorded telemetry data by {car}**_ 
> _so that I can **analyse {car} performance**_"

#### Tasks
1. Implement ``IRepository<Telemetry>`` in a TDD fashion, using ``telemetry.json`` as test data.
2. Complete ``Get()``, ``GetByChassis(string chassis)`` and ``GetByLap(int lap)`` methods in ``TelemetryController.cs``.
3. Add a method for obtaining details of the fastest lap recorded.
4. **[Optional]** Add a basic UI for comparing lap-by-lap telemetry data between CH1 and CH2. The UI should consist of a list of laps, a section for each car, a comparison panel comparing lap time deltas/fuel burn. **Don't spend any time on styling - it just has to be functional!**

#### Acceptance Criteria
 - _**/api/telemetry/get**_ returns all telemetry.
 - _**/api/telemetry/chassis/{chassis}**_ returns all telemetry for a single car.
 - _**/api/telemetry/lap/{lap}**_ returns all telemetry for a single lap.
 - the API has a method to obtain the fastest lap.
 - solution is covered by unit tests.

---

### Story MR-002

> "_As a **Race Engineer**_
> _when a **{car} crosses the start/finish line**_
> _I want to **record telemetry data**_
> _so that I can **react to changing conditions during the race**_"

#### Assumptions
- Each lap is unique, and records a maximum of 2 cars.
- The same car can not be tracked more than once per lap.

#### Tasks
1. Add a method to ``TelemetryController.cs`` for accepting new lap to the collection.
2. Ensure that any duplicated telemetry is handled appropriately.

#### Acceptance Criteria
 - _**/api/telemetry/post**_ allows a new telemetry item to be added to the repository.
 - _**/api/telemetry/lap/{lap}**_ returns all telemetry for your newly added lap.

**Please Note: We are not expecting you to persist your changes to a database. An in-memory stub will do!**



## Additional stories
These stories are open and optional, but we recommend that you **pick at least one** to make your application competitive:

### Story MR-003 (optional)

> "_As a **Race Engineer**_
> _when **our telemetry repository is offline**_
> _I want to **ensure new telemetry data is added to a queue**_
> _so that **we can record the data when connectivity is restored**_"

#### Tasks
1. Add end-to-end asynchronous capabilities to your solution.
2. Add a queue to spool telemetry data writes in the event the repository is offline.

---

### Story MR-004 (optional)

> "_As a **Vehicle Science Engineer**_
> _I want **a living document for the Telemetry API**_
> _so that I can **implement it in my own solutions**_"

#### Tasks
1. Add some form of live API documentation (e.g. Swagger).

---

### Story MR-005 (optional)

> "_As a **Vehicle Science Engineer**_
> _I want to **identify slow pit lane in-laps and out-laps**_
> _so that **average calculations for normal laps aren't skewed**_"

#### Assumptions
- Pit laps always include a tyre change.

#### Tasks
1. Create a filter for identifying slow laps where the car was entering/exiting the pit lane.

---

### Story MR-006 (optional)

> "_As a **Race Engineer**_ 
> _I want to **predict the performance of the car**_
> _so that **I can make tactical decisions during the race**_"

#### Assumptions
- the cars run with a minimum of two different tyre compounds per race. 
- a hard tyre compound lasts more laps and heats up more slowly than the soft tyre compound.

#### Tasks
1. Create a method for calculating average kg/lap fuel burn.
2. Create a method for calculating average tyreDeg/lap tyre degradation for **both** tyre compounds.
3. Create a method for calculating average tyreTemp/lap tyre temperature increase for **both** tyre compounds.

---

### Story MR-007 (optional)
- Go wild! Add a feature of your own design, providing a simple User Story to describe the feature that you have added.



## Top Tips
- We are looking for clean, reabable code that is easy to understand without comments.
- You should make best efforts to cover your code with Unit Tests. We are looking for code written in a TDD fashion.
- **Check in little and often**, referencing the Story # you are working on - we like to see how your solution evolves.
- We use xUnit and Moq here at Manor Racing. We've added the references, but feel free to add your own.
- Make it work, Make it right, Make it fast :)

Good luck - we are looking forward to reviewing your work.

**Software Engineers of Manor Racing**
