# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged:

  I attempted to add a new toy using the form in the browser. Looking at the console and network I was able to see that we had a 500 internal server error.

  This prompted me to look at my server logs and see what happened on the back-end when I attempted to create my toy. 

  There was an error message about an uninitalized constant in toys_controller at line 10. 

  I went into the toys_controller.rb file and looked at line 10 in the create method. There was a typo "Toys.create" was in the file instead of the singular Toy.create because we are creating a new instance of the class Toy. 

- Update the number of likes for a toy

  - How I debugged:

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged:
In the browser I hit donate to Goodwill got a 404 error that the toy was not found

Then I checked the database to make sure the toy existed

Then I checked the routes.rb file to ensure that an appropriate route existed. I updated the routes.rb file to resources :toys and removed the only qualifer. 

I then attempted to donate the toy agian and it was gone from the front-end. So I checked to make sure that it was also gone from the back-end. 