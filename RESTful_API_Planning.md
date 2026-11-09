# Travel_Calculator_API_Planning

# API Selection

For this assignment, I have chosen Frankfurter API. It is an API that houses exchange rates to over 200 currencies. I chose it to get experience using mathematic equations in Python.

# Endpoint Mapping

In the following section, you will notice that I refrained from using the CRUD verb names in the functions to abide by the CRUD names principle of REST. Errors will be handled throughout all this functionality; see more details in the Data Flow section. A first draft of the methods included is below:

•	newBudget – This POST endpoint will serve as the CREATE part of CRUD. It allows the user to create a budget for an upcoming international trip using real-time exchange rates. It will accept the total amount of money in the budget and the target currency that we will be converting it to. Note that it does not take the user’s base currency as an argument; the plan is to have the user set the base currency beforehand. It will return a JSON to the base amount and exchanged amount.
•	newLineItem – This will be the UPDATE endpoint. It allows the user to enter in a transaction with the amount spent on it in the target country’s currency and have that amount taken out of their budget. It will take a description (string) of the expense and the floating-point value for the amount spent. It will return the budget with the line added and the total budget amount reduced.
•	exchangePair – There are a variety of native GET endpoints included in the documentation for Frankfurter. This is the most important of them; I will include documentation on the rest. This endpoint allows to user to GET (READ) a specific exchange rate between two currencies using the native rate/{base}/{quote} functionality.
•	removeLineItem – This is the DELETE function. It will allow you to remove a line item from the budget and have that amount added back into the master budget. You got a refund! It will most likely take the id of the line item (an automatically incremented value) to remove a specific line item and return the new budget.

# Data Flow

	I will implement a UI where the user can press a button that corresponds with the action they wish to do. I will then use text fields and dropdown menus to extract the necessary information, package it into a JSON file, and feed it to the corresponding function. Value and type errors will be handled through the UI, and asynchronous requests will be implemented so that if a user enters an incorrect value, it will give them an informative error message and let them try again.
  
# Form Handling

	There will be a submit button in the UI that lets the app know when the user is done entering info and will then put the responses into JSON format. The form controls will be relatively strict; the user will need to choose from a hard-coded list for constant elements (such as currency or date) to limit format errors. They will use only float values for amounts
  
# Technology requirements

	I will import create_engine, sessionmaker, Column, Integer, String, DateTime, Float, and Session from sqlalchemy and sqlalchemy.orm. I will need all these libraries to maintain the database of budgets for the user. From flask, I will need to import Flask, request, and jsonify. These are the standards libraries needed for creating RESTful APIs in Python (at least to my knowledge). I will also be using pytest to test my app. I think I will need to use BaseModel and Field from the pydantic library to implement some desired functionality, but I may be able to go without it. I will need tk and messagebox from the tkinter library for the UI.
  
# Implementation steps

	I plan to follow these steps to complete the application:
1.	Set up the development environment – At this stage I will install flask and pytest in the project folder.
2.	Create the framework – Here I will create and begin coding the different project files. This will include but is not limited to the main app, the ui, the database functionality, the frankfurter functionality and the travel database as well as the test app.
3.	Create the SQL Lite database for budgets and expenses
4.	Implement Frankfurter functions – Here I will use the requests library to fetch currencies, exchange rates, currency codes, etc. to be used in the main application
5.	Create main application – This is the part where I test my mettle. All of the main functionalities will live here, including all of the POST and GET endpoints I plan to have in the API. At this stage, it would be smart to test the endpoints with curl functions before making the UI
6.	Use tkinter to make a user interface that is easy to use for non-technical people.
7.	Test the API with pytest
