# Advanced State Management Sprint Challenge

**Read these instructions carefully. Understand exactly what is expected _before_ starting this Sprint Challenge.**

This challenge allows you to practice the concepts and techniques learned over the past sprint and apply them in a concrete project. This sprint explored **advanced state management**. During this sprint, you studied **the reducer pattern, and redux**. In your challenge this week, you will demonstrate your mastery of these skills by creating the **Smurf Village Database**!

This is an individual assessment. All work must be your own. Your challenge score is a measure of your ability to work independently using the material covered through this sprint. You need to demonstrate proficiency in the concepts and objectives introduced and practiced in preceding days.

You are not allowed to collaborate during the sprint challenge. However, you are encouraged to follow the twenty-minute rule and seek support from your TL if you need direction. 

_You have **three hours** to complete this challenge. Plan your time accordingly._

## Introduction

In this challenge, you are to build a Smurfs village database utilizing Redux as your state management system. Build this challenge from the ground up using what you have learned about state management.

### Commits

Commit your code regularly and meaningfully. This helps both you (in case you ever need to return to old code for any number of reasons) and your team lead as the evaluate your solution.

## Interview Questions

Be prepared to demonstrate your understanding of this week's concepts by answering questions on the following topics. You might prepare by writing down your own answers before hand.
1. What problem does the context API help solve?

   `It allows access to state throughout the app rather than only by using the top-down passing through prop drilling.`

2. In your own words, describe `actions`, `reducers` and the `store` and their role in Redux. What does each piece do? Why is the store known as a 'single source of truth' in a redux application?

   `Actions: Actions define the types of calls sent to the reducer as well as determines the data sent through payloads and lets us run functions on the data, such as using thunk to run axios requests.`

   `Reducers: Reducers are a means to handle state globally and manipulate it through defined action types and return the desired data.`

   `The 'Store': The single source of truth, as its called, is that because when created we pass state into it, and then wrap our application or components in a Provider which gives them access to that state through the store rather than passing down through props. Every component that has access to the slice of state through a provider will go to that provider for state, rather than up to the parent or grandparent through props.`

3. What is the difference between Application state and Component state? When would be a good time to use one over the other?

   `Application state is global. A light/dark theme or Username might want to be global. Component state is local to the specific component like Form state. Separation of concerns mostly. The component that renders the App Header doesn't need access to the state holding form values in a separate component.`

4. Describe `redux-thunk`, what does it allow us to do? How does it change our `action-creators`?

   `It takes our synchronous flow and turns it into async-chronous flow, which allows us to utilize async to make api calls inside of our action creators. A Thunk is a Function that returns another function`

5. What is your favorite state management system you've learned and this sprint? Please explain why!

   `Probably Redux with Thunk because it's really cool to do the api calls in the action-creators. Context API isn't bad but I really don't like the syntax for it. Context API is pretty similar to the store in Redux in that you wrap .Providers around the components you want to have slices of state, or 'contexts', and it probably is a lot simpler to use than Redux in that you don't have to connect state to props. `

You are expected to be able to answer questions in these areas. Your responses contribute to your Sprint Challenge grade. 

## Instructions

### Task 1: Project Set Up

- [ ] `fork & clone` this repository.
- [ ] `cd` into the forked copy of this repository.

**Setting up the CodeGrade webhook**

Go [here](./CodeGrade-webhook.md) to setup the CodeGrade webhook before you begin.

#### Setup Client Code
- [ ] **LOOK** at your `src` directory and notice it's just a plain ol' React App that we've built using `create-react-app`.
- [ ] **RUN** `npm install` to retrieve all `client-side` the dependencies.
- [ ] **RUN** `npm start` to fire up your React application. There ought to be a pretty little message awaiting you welcoming you to the app. `Follow` the prompting.

**LOOK** at all the files you've been given for this project. Note that you will be interacting with an api during this project. Below is documentation on how to interact with the **API**.

#### Resource: API documentation 

##### GET '/smurfs'

- [ ] Retrieve an array all the Smurfs in the Smurf DB by writing a `GET` to the endpoint `/smurfs`.
- [ ] Double check that your response from the server is an array of smurfs.

```js
[
  {
    id:"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9",
    name:'Poppa Smurf',
    position:'Village Leader',
    nickname: 'Pops',
    description: 'Papa is the practical village leader and the father figure of 100 or so young Smurfs. He is easily identified by his red Smurf hat, pants, and a shortly-trimmed white beard and moustache.'
  }
];
```

##### POST '/smurfs'

- [ ] Design the functionality to add a smurf to the Smurf DB you'll need all five fields. `name`, `position`, and `nickname`, `description`.

Example of the shape of data to be sent to the `POST` endpoint. Note that id does not need to be sent and will be generated on the server:

```js
{
  name:'Poppa Smurf',
  position:'Village Leader',
  nickname: 'Pops',
  description: 'Papa is the practical village leader and the father figure of 100 or so young Smurfs. He is easily identified by his red Smurf hat, pants, and a shortly-trimmed white beard and moustache.'
}
```

- [ ] Double check to make sure that a smurf is created correctly once your functionality is built out.

Initially Brainey will be in the array, but it takes more than one smurf to make the village. Be sure to add a few smurfs to populate our smurf village.

**HINT** if you are going to be working on Stretch Problem, you'll need to use that unique `id`.

Example of object created in Smurf DB:

```js
[
  {
    name:'Poppa Smurf',
    position:'Village Leader',
    nickname: 'Pops',
    description: 'Papa is the practical village leader and the father figure of 100 or so young Smurfs. He is easily identified by his red Smurf hat, pants, and a shortly-trimmed white beard and moustache.'
  },
  {
    id:"JzdWIiOiIxMjM0NTY3ODkwIiwibmFtZ",
    name:'Smurfette',
    position:'Beautician',
    nickname: 'Smurfette',
    description: 'Smurfette\'s role in the village is that of any other smurf; chores, and helping out where she can, but for her specifically, she is often seen to be very active in organizing events.'
  }
];
```

### Task 2: Project Requirements
Your finished project must include all of the following requirements:

- [ ] Plan and implement how you are going to manage your state for your application
- [ ] You _must_ use Redux as your state management system
- [ ] Complete the tasks listed within:
        * `./reducers/index.js`
        * `./actions/index.js`
        * `./index.js`
        * `./App.js`
        * `./components/AddForm.js`
        * `./components/Smurf.js`
        * `./components/SmurfDisplay.js`
- [ ] You completed application should do the following:
        - Fetch and display data from the included server code on mounting.
        - Provide the user a form for adding in the Name, Position, Nickname and Description of a new Smurf.
        - Allow new smurfs to be added to the list when the submit smurf button is pressed.
        - Displays an error alert when name, position or nickname is not included in the submission.
        - Include the word "Error" and "name/position/nickname" in the rendered error alert as approprate.
        - Does NOT display an error alert when description is left blank.
        - Display an error alert if a smurf is submitted with a name already assigned to a smurf.
        - Include the word "Error" and the returned server error message in the rendered error alert as approprate.
        - DO NOT REMOVE ANY data-testid FIELDS FROM THE CODE. These fields are used for internal grading of your sprints. While we don't recommend using testid in most cases, it is necessary our grading systems currently.

In your solution, it is essential that you follow best practices and produce clean and professional results. You will be scored on your adherence to proper code style and good organization. Schedule time to review, refine, and assess your work and perform basic professional polishing including spell-checking and grammar-checking on your work. It is better to submit a challenge that meets MVP than one that attempts too much and does not.


### Task 3: Stretch Goals 

After finishing your required elements, you can push your work further. These goals may or may not be things you have learned in this module but they build on the material you just studied. Time allowing, stretch your limits and see if you can deliver on the following optional goals:

* [ ] Build a smurf profile page with using react-router and dynamic url params  
* [ ] Using React Testing Library, test one or more of your components (not any component that fetches data though)

## Submission format

Follow these steps for completing your project.

- [ ] Submit a Pull-Request to merge <firstName-lastName> Branch into master (student's  Repo). **Please don't merge your own pull request**
- [ ] Add your team lead as a reviewer on the pull-request
- [ ] Your team lead will count the project as complete after receiving your pull-request