**Customer-Billing-and-Rewards-Service**

**Technical Specifications**

JDK Version: 11
Data Storage: H2

**Project Setup Guidelines**

Download and set up the Maven project.
Open git bash and change to the directory customer-rewards-service.
Use the ls command to list all files within the directory.
Execute mvn clean install to build the project.
To launch the application, run docker-compose up from git bash.

**Verifying the Application**

Health Check: App Health Status
API Documentation: Swagger UI
Project Artifacts Folder

The project-artifacts folder contains:

Class and Sequence Diagrams
JSON files for Customers, Transactions, and Monthly and Quarterly Reports. These are obtainable through the Swagger UI.

**Domain Models**

Customer: Houses basic customer information.
Transaction: Contains monthly transaction data, and has a Many-to-One relationship with Customer. Reward points are calculated before saving a transaction.

**API Controllers**

CRUD operations are available via CustomerController and TransactionController.
RewardSummaryController has APIs for both monthly and quarterly reports, accepting 'month' and 'quarter' as parameters.

**Performance**

The quarterly report functionality utilizes parallelStream for efficiency.
Performance should be benchmarked, especially for handling large datasets.

**Service Architecture Considerations**

For complex models involving more tables, the service could be split into customer-service and billing-service.
**Data Persistence and Caching**

Reports are not saved to the database by default. This can be updated if needed.
Consider using local or centralized caching to avoid repeated database calls for generating reports.
Note: DTO transformation is not implemented in this project.

**API Endpoints and Examples**

Create Customer Endpoint: POST Example Request and Response
List All Customers: GET Example Response
Create Transaction Endpoint: POST Example Request and Response
Monthly Reports: GET Example Response
Quarterly Reports: GET Example Response

**Additional Information**

After the app is active, you can view all available endpoints at: Swagger UI
For more details like diagrams and endpoint responses, refer to the project-artifacts directory.



**Create Customer End Point**: http://localhost:8080/rewards/api/v1/customers Method: POST

**Create Customer Request Example**:
{
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
}

**Create Customer Response**:
{
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
}

**Get All Customers Endpoint**: http://localhost:8080/rewards/api/v1/customers Method: GET

**Get All Customers Response**:

[
{
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
},
{
"id": "222-22-2222",
"firstName": "Chris",
"lastName": "Tipton",
"address": "300 Oak Crest Rd, Lafayette, LA 11111"
}
]

**Create Transaction Endpoint**: http://localhost:8080/rewards/api/v1/transactions Method: POST

**Create Transaction Request Example**:
{
"customer": {
"id": "111-11-1111"
},
"billingDate": [2022, 2, 28],
"billingAmount": 75.0
}

**Create Transaction Response**:
{
"id": "4688a4a6-4228-42bf-8bf1-ddaeaa4b5d4f",
"customer": {
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
},
"billingDate": "2022-02-28",
"billingAmount": 75.0,
"rewardPoints": 25
}

**Get Monthly Report Endpoint**: http://localhost:8080/rewards/api/v1/monthlyreport?month=february Method: GET

**Get Monthly Report Response**:

[
{
"customer": {
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
},
"totalPoints": 25
},
{
"customer": {
"id": "222-22-2222",
"firstName": "Chris",
"lastName": "Tipton",
"address": "300 Oak Crest Rd, Lafayette, LA 11111"
},
"totalPoints": 40
}
]

**Get Quartery Report EndPoint**: http://localhost:8080/rewards/api/v1/quarterlyreport?quarter=first Method: GET

**Get Quarterly Report Response**:

[
{
"customer": {
"id": "222-22-2222",
"firstName": "Chris",
"lastName": "Tipton",
"address": "300 Oak Crest Rd, Lafayette, LA 11111"
},
"totalPoints": 110
},
{
"customer": {
"id": "111-11-1111",
"firstName": "Peter",
"lastName": "Pan",
"address": "200 Oak Crest Rd, Lafayette, LA 11111"
},
"totalPoints": 115
}
]
