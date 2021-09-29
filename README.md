# Brewery API Test Report

# Task 1 description
Given the Brewery's API, the task was to found any present bugs and/or quality concerns.  
Test was performed manually using the API's documentation on Swagger (previously raised using Docker).  
API consisted of 3 GET requests:
* Get a single brewery ("/breweries/{id}")
* Search breweries based on search term ("/breweries/search")
* List breweries using different params ("/breweries")

## Bugs found
The following bugs were found:
#### GET /breweries/{id]
1. Response 404 after consecutive requests (Bug ID: 0001)
2. API returns valid data with invalid param (Bug ID: 0002)
#### GET /breweries/search
1. API returns server error after using param with more than 5 characters (Bug ID: 0003)
#### GET /breweries
1. Ascending sort not working correctly (Bug ID: 0004)
2. Descending sort not working correctly (Bug ID: 0005)
3. 'Type of brewery' shows invalid option (Bug ID: 0006)
4. PageSize shows one less object than the number requested (Bug ID: 0007)

#### Please see the bug report for more details on bugs and the way of reproducing them.
[Click here to read the bug report](https://drive.google.com/file/d/1LqmmjJDR80MKCB67KwbPKGcPzwwkLw-n/view?usp=sharing)

# Task 2 description 
The task was to create some tests using a framework of preference. As I don't have that much experience on automation coding for the backend, I've used [Postman](https://www.postman.com/) as tool for creating a Collection of requests that includes automated tests in it.

### Dependencies & Preconditions
* Postman is necessary
* Server must be raised

### How to run the collection
1. Download the 'BreweryAPI.postman_collection' file from this repository.
2. Open Postman and choose any Workspace
3. Import the Collection
4. Click on the three dots menu that appear at the right of the Collection's name when you hover over it
5. Select the option 'Run collection'
6. Click on 'Run Brewery API'

### Comments
* Collection contains both positive and negative requests (meaning that some params are correct and other are incorrect intentionally) to see how the API reacts in every case.
* Some tests fail because of the bugs found.

# Additional notes and observations
Bugs reported are the ones that could been identified with little to no context. For a better testing performance much more information about the scope, the usage of the API and the business, is needed.  
With that been said, there are some suggestions that can be listed:
* Search (GET /breweries/search) is done by similarity, which is OK if the term used is not an existing one. When the param requested is an existing one, meaning that there are objects that contain that exact string on their body (example: 'Enola'), the search is done by similarity as well causing the response to have a lot of unnecessary data. This can be messy for the user and might interfere with the performance.
* For avoiding the appearence of bugs it is necessary to think of a Testing Plan that includes Test Cases to cover every possible case that the API could go through. It would be good to consider to include those Test Cases in a Regression Test suite so they can be runned regulary, and make sure that bugs can be identified early and avoid them to appear in advanced stages of the project.
* Unit and automation tests could be added to help the job of the developers and prevent those bugs to happen. The only bugs that should appear are the ones that weren't considered in the Test Plan's Test Cases.
