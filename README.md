# Goldfish

Final project for CS465/565: Full Stack WebApp for Scheduling and To-do lists. 

### Scheduling algorithm 

At set time intervals, all priorities will decrease by 1 (yielding a higher priority task). This ensures quad 4 tasks eventually see the light of day. When a non-quad1 task reaches 0, it is moved into the next quadrant up. Every day, the top 5 tasks are pulled from the master list. Top 5 tasks first queries and pulls any quad1 tasks. If there are no more quad1 tasks, the remaining available slots are filled by quad2 and quad3 tasks (or quad4, if there are not enough quad2/3 tasks). 50% of the available slots will be filled by a quad2 task and 40% (rounded up) will be filled by quad3 tasks. Most quad4 tasks will only be completed through promotion to quad 2 or 3, not through assignment, unless the user has an abnormally empty schedule.

### Four Quadrant System

Quadrant 1: Urgent and Important. Items here need to be completed soon and the user has marked as important. These should be completed before anything else the user does. If these are present, they take up 100% of the users time and priority. 
Examples: project deadlines, meetings, and important events.

Quadrant 2: Non-urgent but Important. Items here are critically important but not due soon. These should be encorporated into the to-do list in round-robin style chunks so that they do not reach quadrant 1, but do not absorb the users entire day if there are quadrant 3 or 4 tasks present. If these are present, they take up 50% of the the time and priority not occupied by quadrant 1 tasks. 
Examples: Far-off deadlines, professional development, and important tasks that do not have a submission date.

Quadrant 3: Urgent but not-Important. Items here need to be completed soon but are not important. These should be completed by the user daily, but should not dominate the to-do list. If these are present, they take up 45% of the time and priority not occupied by quadrant 1 tasks. 
Examples: Non-important or recreational events (like a concert), repetative tasks, optional meetings, busy work.

Quadrant 4: Non-urgent and not-Important. Items here are things that need to get done, but do not have a deadline nor are they critical. These should be completed at some point, but should not be done if there are more important things to do. If they are present, they take up 5% of the time and priority not occupied by quadrant 1 tasks. 
Examples: non-eessential chores (like returning cans to recycling center), purchasing desired items (like getting a new pair of sneakers when current pair are worn out, but still functioning), and activities like rearranging your room or starting a fun, but non-critical project. 


## Prototypes

### Task object

This is the actual task that will be saved and moved around within the webapp

| Task | sub-obj | sub-obj |
| --- | --- | --- |
| name [string] | | |
| quad [int] | | |
| prio [int] | | |
| due [obj] | date [date/time] | time [date/time]|
| location [obj]| name [string] | address [string] |
| comment [string] | | |
| complete [bool] | | |
| subTask [obj] | | |

name: Self-explainatory.

quad: See Quadrant description below.

prio: Short for priority; ranked 1 through 99 with 1 being the top priority for that quadrant.

due: Date and time added here.

location: Option for name of location and address.

comment: Any addtional comment the user would like to attach to this task.

complete: True/False.

subTask: Task object that needs to be completed to complete this task. **MAY BE OUTSIDE THE SCOPE OF THIS CURRENT PROJECT VERSION

### Task List object

This is the meta-list that stores, sorts, and is referenced for pulling the daily to-do list. Uses the four quadrant method.

| Task List |
| --- |
| quad1 [1-99] |
| quad2 [1-99] |
| quad3 [1-99] |
| quad4 [1-99] |

### Daily To-Do object

This is the daily list of to-dos pulled from the priority categories of the master list (Ben found that 5 is a reasonable number, however this could be adjusted according to user preference). 


| Daily Todos |
| --- |
| item1 [string]|
| item2 [string] |
| item3 [string] |
| item4 [string] |
| item5 [string] |
