# take-home-assessment
A Take Home Assessment we could give to potential candidates

### Objective
Pick your favorite technology to create a simple RESTful service to create and maintain to-do lists. Use this assessment to demonstrate your understanding of solid coding practice. Plan for about two hours of work, though you are welcome to spend as much time as you like!

### Spec

#### Create a Todo List

Create a todo list with a name, and optionally a list of tasks (tasks can be added later)

Examples:

```
  POST /todo HTTP/1.1
  Content-Type: application/json
  
  { “name” : “World Domination Checklist” }
```

```
  POST /todo HTTP/1.1
  Content-Type: application/json
  
  { “name” : “World Domination Checklist”,
    "tasks" : [
      { "name" : "Collect all the world's oranges" },
      { "name" : "?" },
      { "name" : "Profit!" }
    ]
  }
```

A todo list has at least the following properties:

* name - The name of the todo list
* tasks - A list of Tasks
* totalTime - The amount of time needed to complete all tasks in the list

#### Retreive a Todo List

```
  GET /todo/{id} HTTP/1.1
```

#### Update a todo list

```
PATCH /todo/{id} HTTP/1.1
Content-Type: application/json

{ "name" : "Lehi Domination Checklist" }
```

#### Delete a todo list

```
DELETE /todo/{id} HTTP/1.1
```

#### Create a todo list item

```
POST /todo/{id}/item HTTP/1.1
Content-Type: application/json

{ “name” : “Draw Picture for Mom”, “time” : "32h", "deadline" : "2020-10-17T11:59:59" }
```

A todo list item has at least the following properties:

* name - The name of the item
* time - The amount of time this item will take
* deadline - The ISO-standard due date
* completed - Whether or not the task is complete

#### Retreive, Update, Delete todo list items

As you might imagine them

#### Get Today's Work

Responds with uncompleted items in order of deadline, segmented by "overdue" and "due today"

Example Request:

```
GET /work-for-today HTTP/1.1
```

Example Response:

```
{
  "overdue" : [
    { "id" : "00f7a403-feea-49ae-9d13-2c9e20f1d537", "name" : "Find My Keys", "deadline" : "2017-10-12T08:00:00" }
  ],
  "due_today" : [
    { "id" : "f93a8f3d-60b9-4678-a9e9-d87c3466b516", "name" : "Donate Plasma", "deadline" : "2017-10-17T08:00:00" }
  ]
}
```

#### Stretch Goals for the Bored

* _Recurring Tasks_: Add tasks to a list that need to be completed on a recurring basis
* _Sub tasks, Sub-Sub Tasks, Sub-Sub-Sub Tasks_: Add tasks to tasks
* _Prioritization_: Add tasks that trump other tasks in priority

* _Security_: Make it secure
* _Performant_: Make it scale

#### What should I code this in?

Really, anything you can send us a binary with instructions on how to run! However, at Workfront, we are well familiar with two back-end stacks--Spring Boot and AWS Serverless with Node. Coding it up in one of those might create a richer conversation during your interview.
