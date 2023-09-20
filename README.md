JDK Version: 11
Data Storage: H2

**Run Project Steps:

Download and import the project as an Maven project.
Open git bash and go to the directory. Use 'ls' to check files in this folder.
Execute 'mvn clean install'.
To start the app, run 'docker-compose up' in git bash.
Check App Health:
**
App Health: http://localhost:8080/actuator/health
API Documentation: http://localhost:8080/swagger-ui/
Project Artifacts Folder:

Contains Class and Sequence Diagrams.
Provides json files for Customers, Transactions, Monthly and Quarterly Reports. These can be downloaded via the swagger UI.
Model Explanation:
**Customer: Basic profile info.
Transaction: Monthly transaction details, linked to Customer. Reward points are calculated before saving.
APIs:

CRUD operations available for Customer and Transaction.
RewardSummaryController has APIs for monthly and quarterly reports. The 'month' or 'quarter' is taken as an input parameter.
Performance:

Quarterly reports use parallel streams for better performance.
Further Considerations:

Break service into 'customer-service' and 'billing-service' for more complex domains.
Monthly and Quarterly reports are not saved in the database.
Consider caching to improve performance.
No DTO Transformation Done.

**API Endpoints:

Create Customer: POST http://localhost:8080/rewards/api/v1/customers
Example Request and Response provided.
List Customers: GET http://localhost:8080/rewards/api/v1/customers
Example Response provided.
Create Transaction: POST http://localhost:8080/rewards/api/v1/transactions
Example Request and Response provided.
Monthly Report: GET http://localhost:8080/rewards/api/v1/monthlyreport?month=february
Example Response provided.
Quarterly Report: GET http://localhost:8080/rewards/api/v1/quarterlyreport?quarter=first
Example Response provided.
** Note:

View all available endpoints at: localhost:8080/swagger-ui/
Refer to 'project-artifacts' for additional resources.