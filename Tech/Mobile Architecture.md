---
type:
  - Tech
tags:
  - Mobile
  - Architecture
  - Android
published: true
created: 2023-10-27 21:26
modified: 2023-12-19T12:07:00
folder: Tech
---
# Mobile app architecture review
1. **Presentation layer**
- Contains components for the UI along with the components for UI processing.

2. **The business layer**
- Is concerned with the logic and rules responsible for data exchange, operations and workflow regulation

3. **The data layer**
- Includes all the data utilities, service agents and data access components to support data transactions.
# Separation of concerns 
Separation of concerns (SoC) is a design principle for separating app into distinct sections such that each section addresses a separate concern:
- These layers should be loosely coupled
- Changes in one layer having limited or no impact on any other layers

![Imgur|700](https://i.imgur.com/dr0PExt.png)

# Single responsibility vs Separation of Concerns

**Single responsibility**
A component should have only one reason to change if the role that utilizes component determine change is necessary. Therefore, we should divide responsibility by role (vertically)

**Separation of concerns**
To realize a feature, we need to rely on a mix of infrastructure, application and domain layer logic. SoC urges us to divide the "technical" implementation details of a feature.To do this, we can implement a layerd architecture (horizontal)

# Architecture
## Model View Controller

- **Model**: responsible for managing the data of the application. It receives user input from the controller.

- **View**: renders a presentation of the model in a particular format.

- **Controller**: responds to user input and perform interactions on data model objects. Controller receives input, optionally validates it, and then passes the input to the model

![Imgur|410](https://i.imgur.com/ooCv2LQ.png)

## Model View Presenter

- **Model**: represents a set of classes that describes the business logic and data. It also defines business rules for data means how the data can be changed and manipulated.

- **View**: represents the UI components. It is only responsible for displaying data that is received from the presenter as the result. This also transform the models into UI

- **Presenter**: responsible for handling all UI events on behalf of the view. This receives input from users via the View, then process the user's data with the help of the Model and passes the results back to the View

![Photo|550](https://www.researchgate.net/publication/348792766/figure/fig3/AS:984420416761864@1611715525181/MVP-design-pattern-diagram.jpg)

## Model View ViewModel

**MVVM** stands for Model-View-View Model. This pattern supports two-way data binding between View and View Model.
- **Model**: holds data of the applications. It cannot directly talk to the View. Generally, it's recommended to expose data to ViewModel through Observables.

- **View**: represents the UI of application devoid of any application logic. It observes ViewModel

- **ViewModel**: acts as a link between Model and View. It's responsible for transforming data from the Model. It provides data streams to the View. It also hooks or callbacks to update the View. It'll ask for the data from Model.

![Photo|660](https://androidcoban.com/wp-content/uploads/2018/10/android-mvvm-livedata-viewmodel-retrofit.png)

## Model View Intent
**MVI** stands for Model-View-Intent. MVI imagines user as a function, and models a unidirectional data flow based on that.

- **Model**:  other than representing the data and the business logic of the application model maintains a state which can be changed through the actions of the user.

- **View**: reprsents the UI of application which consists of Activities and Fragments. It accepts different model states and displays them as a UI

- **Intent**: do not confuse it with Android Intent, it's the intention to perform an action either by the user or app itself

![Photo](https://miro.medium.com/v2/resize:fit:1400/0*eDA_holcZgQBU6e3)

## Android app architecture

Based on [[Clean Architecture]]
- **Presentation layer**: also called UI layer. Its role is to display application data on screen. Whenever data changes, UI should update to reflect the changes.
- **Domain layer**: responsible for encapsulating complex business logic, or simple business logic that is reused by multiple ViewModels
- **Data layer**: contain data repositories.

![Photo|700](https://miro.medium.com/v2/resize:fit:720/format:webp/1*cWigoCU4Q_O25hscjOq-fg.png)

## React Redux

![Imgur](https://i.imgur.com/DyEsiNJ.png)

- **Store**: a state container that holds on to app state. It holds an immutable reference representing the entire state of application and can only be updated by dispatching an Action to it
- **Actions**: contain info to be sent to the Store. They represent how we want our state to be changed.
- **Reducers**: since neither Actions nor Store update state themselves, Reducers do it. They simply take an Action and State and emit a new State. 